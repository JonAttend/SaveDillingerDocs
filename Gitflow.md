# Git FLow
## Commandes générales Git

### Récupérer un dépôt distant
`git clone <my-url-project>`
```js
Cloning into `<my-url-project>`...
> remote: Counting objects: 10, done.
> remote: Compressing objects: 100% (8/8), done.
> remove: Total 10 (delta 1), reused 10 (delta 1)
> Unpacking objects: 100% (10/10), done.
```  
### Savoir le statut de notre suivi Git
`git status`
>👇 Si vous en 'avance' par rapport à la branch en remote
```js
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
(use "git restore <file>..." to discard changes in working directory)
        modified:   graph.js
        modified:   public/stylesheets/style.css
        modified:   routes/drive.js
        modified:   views/drive.hbs

no changes added to commit (use "git add" and/or "git commit -a")
```
>👇 Si vous êtes à jour
```js
On branch develop
Your branch is up to date with 'origin/develop'.

nothing to commit, working tree clean
```  

### Lister toutes les branches
Local
`git branch`
>👇 A noter que la branch sur laquelle on se trouve est signalée d'un *
```js
* develop
main
```  
Remote
`git branch -r`
>👇 **origin** n'est pas le nom du référentiel distant. Il s'agit plutôt d'un alias **local** défini comme clé à la place de l'URL du référentiel distant.
Cela évite à l'utilisateur d'avoir à taper l'intégralité de l'URL distante lorsqu'il demande un push
```js
origin/24431_menu_section
origin/24438_add_authentification
origin/24697_jquery_not_working_bug
origin/24768_add_auth_page-revert-from-develop
origin/24779_index_template_for_project_groups
origin/24796_generate_index_template
origin/25056_sort_data_json
origin/25081_clean_html
origin/25115_add_filter_searchbar
origin/HEAD -> origin/main
origin/develop
origin/main
```  
 Local + Remote
`git branch -a`
>👇 A noter que les branchs distantes commencent par **remote**
 ```js
* develop
 main
remotes/origin/24431_menu_section
remotes/origin/24438_add_authentification
remotes/origin/24697_jquery_not_working_bug
remotes/origin/24768_add_auth_page-revert-from-develop
remotes/origin/24779_index_template_for_project_groups
remotes/origin/24796_generate_index_template
remotes/origin/25056_sort_data_json
remotes/origin/25081_clean_html
remotes/origin/25115_add_filter_searchbar
remotes/origin/HEAD -> origin/main
remotes/origin/develop
remotes/origin/main
```
### Créer une nouvelle branche
`git checkout -b <my-branch-name>`
>👇 A noter que c'est l'option **-b** qui permet de créer une nouvelle branch et que l'on est automatiquement switch dessus lors de sa création
```js
Switched to a new branch '<my-branch-name>'
```  
### Se déplacer dans les branches
Local
`git checkout <my-branch-name>`
>👇 A noter que checkout s'exécute **sans** option
```js
Switched to branch '<my-branch-name>'
```  
Remote
`Git Pull`
`git checkout --track origin <my-branch-name>`
>👇 A noter que c'est plutôt rare de vouloir récupérer une branche qui n'est pas au même niveau depuis le dépôt distant.
```js
Switched to branch '<my-branch-name>'
```  
### Supprimer une branche
Local
`git checkout <my-branch-name>`
>👇 A noter que checkout s'exécute avec l'option **-d**
```js
Deleted branch <my-branch-name> (was f187012).
```  
Remote
`git push origin --delete <my-branch-name>`
>☝️ UNIQUEMENT dans le cas ou l'on push une branche qu'on ne voulait pas envoyer sur le dépôt distant !

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Dillinger is a cloud-enabled, mobile-ready, offline-storage compatible,
AngularJS-powered HTML5 Markdown editor.

- Type some Markdown on the left
- See HTML in the right
- ✨Magic ✨

## Features

- Import a HTML file and watch it magically convert to Markdown
- Drag and drop images (requires your Dropbox account be linked)
- Import and save files from GitHub, Dropbox, Google Drive and One Drive
- Drag and drop markdown and HTML files into Dillinger
- Export documents as Markdown, HTML and PDF

Markdown is a lightweight markup language based on the formatting conventions
that people naturally use in email.
As [John Gruber] writes on the [Markdown site][df1]

> The overriding design goal for Markdown's
> formatting syntax is to make it as readable
> as possible. The idea is that a
> Markdown-formatted document should be
> publishable as-is, as plain text, without
> looking like it's been marked up with tags
> or formatting instructions.

This text you see here is *actually- written in Markdown! To get a feel
for Markdown's syntax, type some text into the left window and
watch the results in the right.

## Tech

Dillinger uses a number of open source projects to work properly:

- [AngularJS] - HTML enhanced for web apps!
- [Ace Editor] - awesome web-based text editor
- [markdown-it] - Markdown parser done right. Fast and easy to extend.
- [Twitter Bootstrap] - great UI boilerplate for modern web apps
- [node.js] - evented I/O for the backend
- [Express] - fast node.js network app framework [@tjholowaychuk]
- [Gulp] - the streaming build system
- [Breakdance](https://breakdance.github.io/breakdance/) - HTML
to Markdown converter
- [jQuery] - duh

And of course Dillinger itself is open source with a [public repository][dill]
 on GitHub.

## Installation

Dillinger requires [Node.js](https://nodejs.org/) v10+ to run.

Install the dependencies and devDependencies and start the server.

```sh
cd dillinger
npm i
node app
```

For production environments...

```sh
npm install --production
NODE_ENV=production node app
```

## Plugins

Dillinger is currently extended with the following plugins.
Instructions on how to use them in your own application are linked below.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Development

Want to contribute? Great!

Dillinger uses Gulp + Webpack for fast developing.
Make a change in your file and instantaneously see your updates!

Open your favorite Terminal and run these commands.

First Tab:

```sh
node app
```

Second Tab:

```sh
gulp watch
```

(optional) Third:

```sh
karma test
```

#### Building for source

For production release:

```sh
gulp build --prod
```

Generating pre-built zip archives for distribution:

```sh
gulp build dist --prod
```

## Docker

Dillinger is very easy to install and deploy in a Docker container.

By default, the Docker will expose port 8080, so change this within the
Dockerfile if necessary. When ready, simply use the Dockerfile to
build the image.

```sh
cd dillinger
docker build -t <youruser>/dillinger:${package.json.version} .
```

This will create the dillinger image and pull in the necessary dependencies.
Be sure to swap out `${package.json.version}` with the actual
version of Dillinger.

Once done, run the Docker image and map the port to whatever you wish on
your host. In this example, we simply map port 8000 of the host to
port 8080 of the Docker (or whatever port was exposed in the Dockerfile):

```sh
docker run -d -p 8000:8080 --restart=always --cap-add=SYS_ADMIN --name=dillinger <youruser>/dillinger:${package.json.version}
```

> Note: `--capt-add=SYS-ADMIN` is required for PDF rendering.

Verify the deployment by navigating to your server address in
your preferred browser.

```sh
127.0.0.1:8000
```

## License

MIT

**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
