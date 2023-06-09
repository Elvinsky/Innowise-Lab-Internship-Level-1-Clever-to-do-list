<h1>Innowise task. Internship level 1</h1>
<h2>Installation</h2>
<ul>
    <li>Clone the repo</li>
    <li>Navigate to the project root directory</li>
    <li>Run <strong>npm install</strong> to install dependecies</li>
    <li>Run <strong>npm run serve</strong> to launcg the project</li>
    <li>Project will be deployed on the <strong>/localhost:****</strong></li>
</ul>
<h2>
    Task summary is initially given <a href="https://drive.google.com/file/d/18I1PxOxZn2lwm__YeOtMNoWeiXygKwwN/view">Here</a>
</h2>
<h2>Database snapshot</h2>
<p>
    <h3>The project has an initial document called 'users', which stores information about each user. Each user has the following fields:</h3>
    <br>
    <ul>
        <li><strong>email:</strong> a string representing the user's email address.</li>
        <li><strong>id:</strong> a unique identifier for the user.</li>
        <li><strong>password:</strong> a string representing the user's password.</li>
        <li><strong>username</strong>: a string representing the user's username.</li>
    </ul>
    <br>
    <h3>Each user have nested <strong>todos</strong> document with following fields</h3>
    <ul>
        <li><strong>content:</strong> a string representing the content of the todo.</li>
        <li><strong>date:</strong> a timestamp of the date the todo was created.</li>
        <li><strong>done:</strong> a boolean indicating whether the todo is completed or not.</li>
        <li><strong>id:</strong> a unique identifier for the todo.</li>
        <li><strong>name:</strong> a string representing the name of the todo.</li>
    </ul>
    With this data model, each user can have multiple todos, and each todo can be easily accessed and updated.
</p>
<h1>Directories</h1>
<p>
    <br>
├── .browserlintrc<br>
├── .eslitrc<br>
├── .babel.config.js<br>
├── jsconfig.json<br>
├── vueconfig.js<br>
├── src<br>
│   ├── assets - <strong>Assets and pictures</strong><br>
│   ├── components<br>
│   │   ├── Auth - <strong>Authorization components</strong><br>
│   │   ├── Calendar - <strong>Calendat components</strong><br>
│   │   ├── Todos - <strong>Todos components</strong><br>
│   │   └── HomePage.vue - <strong>Home page component</strong><br>
│   ├── scripts<br>
│   │   ├── crudApi.js - <strong>Create Read Update Delete operation for db</strong><br>
│   │   ├── queries.js - <strong>Queries for retrieving data from db</strong><br>
│   │   └── utils.js - <strong>Other utils scripts for project</strong><br>
│   └── store<br>
│       └── index.js - <strong>VueX store configuration</strong><br>
└── firebase.js - <strong>Firebase configuration</strong><br>
</p>

<h3>Made by Nikita Mikhnevich</h3>