---
layout: post
title:      "ReactJS Project: My Hacker News Feed"
date:       2019-06-16 19:20:31 +0000
permalink:  reactjs_project_my_hacker_news_feed
---

Recently, I created a simple Hacker News clone app using AngularJS and decided to rebuild an identical project using ReactJS and Redux. Code migration is a very important aspect of success in the tech industry. Keeping up with new technologies as businesses scale software, mobile applications and web applications is crucial. I'll cover a few key steps of the code migration process from AngularJS to ReactJS.

![](https://cdn.buttercms.com/mm1EznBASzORrNJ9yV9a)

After bootstrapping my ReactJS project, using the `create-react-app` command in the terminal, I installed `react-router-dom` to manage routes, `react-redux` to manage state, and `react-thunk` as middleware. Once my store and middleware were set up, I needed to create an async action to collect a list of Top Stories data from the Hacker News API. In AngularJS this method was a service method.

AngularJS:

-js/app/services/PostsService.js

```
//..
function PostsService($http) {
	this.getTopStories = () => {
		return $http.get('https://hacker-news.firebaseio.com/v0/topstories.json');
	};
	//...
```

ReactJS:

-src/actions/posts.js

```
import { beginDataFetch, endDataFetch } from './dataFetch'

export const fetchPostIdList = () => {
    return dispatch => {
        fetch('https://hacker-news.firebaseio.com/v0/topstories.json', { method: 'GET' })
        .then(response => response.json())
        .then(postIds => {
            dispatch(beginDataFetch())
            dispatch(getTopStories(postIds))
            dispatch(endDataFetch())
        })
    }    
}

const getTopStories = postIds => {
    return {
        type: 'GET_POST_IDS',
        postIds
    };
}
//..
```

In ReactJS in order to manipulate rendering, it is helpful to utilize extra methods that keep track of when async actions begin and end. Here I used a `dataFetch` method to know when the data had been collected. This prevents errors and unnecessary re-rendering.

Because I used an `Item` component and view file in the AngularJS version I transferred the code to a `Item` visual component in ReactJS by copying the `item.html` view file code and converting it to JSX. 

AngularJS:

-views/item.html

```
<div class="item" ng-if="item.data">
	<div ng-switch="item.data.type">
		<div ng-switch-when="comment">
			<div class="item__author">
				<p ui-sref="user({id: item.data.by })">
					<strong>{{ item.data.by }} - {{ (item.data.time * 1000) | date: 'short'}}</strong>
				</p>
			</div>
			<div ng-bind-html="item.data.text"></div>

			<ul class="comments">
				<li ng-repeat="comment in item.data.kids">
					<item id="comment"></item>
				</li>
			</ul>
		</div>
		<div ng-switch-when="story">
			<a class="item__title" href="{{ item.data.url }}" target="_blank">
				{{ item.data.title }} - {{ (item.data.time * 1000) | date: 'short'}}
			</a> 
			<p>	{{ item.data.score }} points by {{ item.data.by }}</p>
			<a class="item__description" ui-sref="post({id: item.data.id})">
				{{ item.data.descendants }} comments 
			</a>
		</div>
	</div>
</div>
```

ReactJS:

-src/components/item.js

```
//...
return (
                <li>
                    {data.type === "comment" ? <div className="item">
                        <div className="item__author">
                            <p>
                                <strong>{ data.by } - { this.formatDate(data.time) }</strong>
                            </p>
                        </div>
                        <div dangerouslySetInnerHTML={{__html: data.text}}></div>
                        
                        <ul className="comments">
                            {data.kids && data.kids && data.kids.map((id) => (
                                <Item key={id} itemId={id} id="comment"/>  
                            ))}
                        </ul>
                    </div>
                    :<div className="item">
                        <a href={data.url} className="item__title" rel="noopener noreferrer" target="_blank">
                            { data.title } - { this.formatDate(data.time) }
                        </a> 
                        <p>	{ data.score } points by { data.by }</p>
                        <Link to="/" className="item__description" onClick={this.handleClick}>
                            { data.descendants } comments 
                        </Link>
                    </div>}
                </li>
            )
						//...
```

As you can see there is a level of similarity from the Angular code to the React code. HTML elements are rendered based on conditional statements. It's important to understand how each front-end framework translates the code into the rendered HTML in the browser in order to recreate an identical project. By using the exact same HTML structures and class names I was able to use an identical CSS file, which produced the same styles and layouts for each project.

Copying the `TopStoriesController` function code from AngularJS project to a `TopStoriesContainer` allowed me to duplicate the `pagination`, `nextPage`, and `previousPage` methods. In ReactJS these methods manipulate the props passed down to the list of `Item` components. Only a slice of 25 items is passed down to be rendered at a time.

AngularJS:

-js/app/controllers/TopStoriesController.js

```
//...
	let ctrl = this;

	ctrl.page = 0;
	ctrl.totalPosts = posts.data.length;
	ctrl.totalPages = Math.ceil(ctrl.totalPosts / 25);

	ctrl.paginatePosts =  () => {
		ctrl.posts = posts.data.slice(ctrl.page * 25, (ctrl.page + 1) * 25);
	};

	ctrl.nextPage = () => {
		ctrl.page++;
		ctrl.paginatePosts()
	};

	ctrl.previousPage = () => {
		ctrl.page--;
		ctrl.paginatePosts();
	};

	ctrl.paginatePosts();
	//...
```

ReactJS:

-src/containers/topStoriesContainer.js

```
//...
    constructor(props) {
        super(props);
        this.state = {
	        page: 0,
	        totalPosts: 0,
	        totalPages: 0
        };
        this.paginatePosts = this.paginatePosts.bind(this);
        this.nextPage = this.nextPage.bind(this);
        this.previousPage = this.previousPage.bind(this);
    }

	paginatePosts(){
	    let ids = this.props.postIds.slice(this.state.page * 25, (this.state.page + 1) * 25);
        return ids;
    }

	nextPage(e){
        e.preventDefault();
        this.setState(({ page }) => ({ page: page + 1 }))
		this.paginatePosts()
	}

	previousPage(e){
        e.preventDefault();
        this.setState(({ page }) => ({ page: page - 1 }))
		this.paginatePosts();
    }
    
    componentWillReceiveProps(){
	    this.setState({
            totalPosts: this.props.postIds.length,
	        totalPages: Math.ceil(this.props.postIds.length / 25)
        })
    }

    render() {
        let ids = this.paginatePosts()
				//...
```

Here I used the `componentWillReceiveProps` method to set the number of total posts and total pages once the list of `postIds` are received as props. The first rendering of posts is automatically set to the first 25 of the total list. Pagination buttons with `onClick` methods handle next and previous pages.

There was alot that went into migrating this simple project. I learned so much and built a clear vision of the similarities and differences between AngularJS and ReactJS. As a JavaScript Developer it is essential to know as many JavaScript Frameworks in your toolbox because they are all out there in the professional world. The ability to translate between these frameworks is another skill altogether. I’m excited to continue practicing this new skill.

Please, feel free to take a peek at the GitHub repos and video comparison of both projects:

[AngularJS](https://github.com/Xplor8r/My_Hacker_News_feed)

[ReactJS](https://github.com/Xplor8r/my_hacker_news_feed2)

[Comparison Video](https://www.youtube.com/watch?v=HQhZP2Y4a4c&feature=youtu.be)

