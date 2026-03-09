[9:37 PM, 3/9/2026] Kaviya💜: let posts = JSON.parse(localStorage.getItem("posts")) || [];

function displayPosts(){

let container = document.getElementById("posts");

if(!container) return;

container.innerHTML="";

posts.forEach((post,index)=>{

let div = document.createElement("div");
div.className="post";

div.innerHTML = `
<p>${post.text}</p>

<button onclick="likePost(${index})">
Like (${post.likes})
</button>

<input id="comment${index}" placeholder="Write comment">

<button onclick="addComment(${index})">
Comment
</button>

<div id="comments${index}">
${post.comments.map(c=>"<p>"+c+"</p>").join("")}
</div>
`;

container.appendChild(div);

});

localStorage.setItem("posts",JSON.stringify(posts));

}

function createPost(){

let text = document.getElementById("postInput").value;

if(text==="") return;

posts.push({
text:text,
likes:0,
comments:[]
});

document.getElementById("postInput").value="";

displayPosts();

}

function likePost(index){

posts[index].likes++;

displayPosts();

}

function addComment(index){

let comment = document.getElementById("comment"+index).value;

if(comment==="") return;

posts[index].comments.push(comment);

displayPosts();

}

displayPosts();
[9:42 PM, 3/9/2026] Kaviya💜: Project Description
This project is a Mini Social Media Platform developed as part of the Full Stack Development Internship.
The application allows users to create posts, like posts, and comment on posts. It also includes a simple user profile page.
The goal of this project is to demonstrate basic social media features and frontend development skills.
Features
User profile page
Create and publish posts
Like posts
Add comments to posts
Simple and responsive user interface
Data stored using Local Storage
Technologies Used
HTML
CSS
JavaScript
Project Structure
Copy code

social-media-app
│
├── index.html
├── profile.html
├── style.css
├── script.js
└── README.md

