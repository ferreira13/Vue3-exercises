## Using Vue CLI for Vue.js Projects

We'll be using Vue CLI, which provides us with a suite of tools for running, minifying, and testing applications. Let's install it globally on our machine using NPM:

```bash
yarn global add @vue/cli
```

After the installation, you'll have access to the `vue` command in your terminal. Now, you need to choose any directory to store your Vue projects. Navigate to that directory and create a new application using the following command:

```bash
vue create helloworld
```

In this command, we use `vue create` to indicate that we want to create a new project. Then, we specify the directory in which our project will be created, in this case, the `helloworld` folder.
Certainly, here's the translated and formatted text in English with Markdown:

---

## Testing Your Vue.js Project

To test your Vue.js project, navigate to the project directory using the `cd` command. Then, specify that you want to run your code in a development environment:

```bash
cd helloworld
yarn serve
```

After the necessary files have been loaded, your default web browser will open, and you can access your project at [http://localhost:8080](http://localhost:8080).

