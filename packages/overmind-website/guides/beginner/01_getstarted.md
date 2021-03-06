# Get started with Overmind

If you are moving from an existing state management solution, please read the release article [Reducing the pain of developing apps](https://medium.com/@christianalfoni/reducing-the-pain-of-developing-apps-cd10b2e6a83c).

To get started with Overmind you have to set up a project. You can do this with whatever tool your framework of choice provides or you can use [webpack](https://webpack.js.org/) or [parceljs](https://parceljs.org/). You can also use [codesandbox.io](https://codesandbox.io/) to play around with Overmind directly in the browser.

```marksy
h(Notice, null, "Due to using the Proxy feature of JavaScript, Overmind does not support **Internet Explorer 11**.")
```


When you have your project up and running install the Overmind dependency by using [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/en/):

```marksy
h(Example, { name: "guide/getstarted/install" })
```

```marksy
h(TypescriptNotice, null, "Overmind requires Typescript version **3.2** or above")
```



Great, we are good to go!

## Our first state

Applications are about state and we are going to introduce our first state, **count**. Typically you would be tempted to isolate this state in your component, but this is exactly what Overmind discourages. In Overmind you primarily define the state of your application outside of your view layer. This gives you several benefits which will become clear as we move on.

Let us imagine we get what we need from Overmind in a component:

```marksy
h(Example, { name: "guide/getstarted/count" })
```

This will of course not work. To make this work we have to create an Overmind application instance and expose it to our component.

```marksy
h(Example, { name: "guide/getstarted/createapp" })
```

Now that we have our application, let us expose it to our component.

```marksy
h(Example, { name: "guide/getstarted/connectapp" })
```

That is it, your component will now render whenever the state accessed changes. Please read more about connecting state to components in the [guides section](/guides).

## Changing state

We want to change our count. To do this we need to create an action. This action will receive a number that we use to change the current count state.

```marksy
h(Example, { name: "guide/getstarted/changestate" })
```

This action can now be called from out component to change the count.

```marksy
h(Example, { name: "guide/getstarted/triggeraction" })
```

By just using the **count** state in the component it will understand that it needs to update when the count changes.

## Creating effects

 State management tools has a tendency to end their introduction here, but Overmind helps you manage one more important ingredient, **effects**. An effect, or side effect, is everything from doing http requests to storing data in local storage. What Overmind helps you with is separating the generic low level APIs of using these effects from your actual application logic inside actions. Let us look at an example. We are going to add a sound when we click the buttons:

```marksy
h(Example, { name: "guide/getstarted/effect" })
```

As you can see we separated the low level generic code of creating a sound from our actual application logic in the action. Think of effects as the API you custom tailor to your application. This improves the readability of your application logic inside actions, you can easily test effects and they can also be mocked out in tests.

## Devtools

At this stage, the benefits of writing application code this way might not be obvious. It is usually when we start to deal with more complexity that the benefits become more obvious. But even with a simple app, there is one big benefit that comes right out of the box. In our **package.json** file, we add the following and the run the script.

```marksy
h(Example, { name: "guide/getstarted/devtools" })
```

You can also explicitly install the devtools with

`npm install overmind-devtools`

and rather:

```marksy
h(Example, { name: "guide/getstarted/devtools_explicit" })
```

This allows you to control the version you want to use.

You can even:

```marksy
h(Example, { name: "guide/getstarted/devtools_concurrent" })
```

By installing the [concurrently](https://www.npmjs.com/package/concurrently) package you can start your development process and the devtools at the same time.

The Overmind devtools provides us with a pretty amazing experience. We get insights into all the state, changes to that state, actions run, which side effects are run and general stats. This visual overview becomes more and more valuable as complexity increases. 

To connect to the devtools simply start the devtools application and refresh your app. If you need to configure where it connects, please look at the [API section](/api/overmind).

## Hot Module Replacement

A popular concept introduced by Webpack is [HMR](https://webpack.js.org/concepts/hot-module-replacement/). It allows you to make changes to your code without having to refresh. Overmind automatically supports HMR. That means when **HMR** is activated Overmind will make sure it updates and manages its state, actions and effects. Even the devtools will be updated as you make changes.

## Summary

You have now stepped your toes into Overmind. Please continue this example to actually display the posts fetched. In the devtools you will see how the component will become quite bloated with dependencies to state, which is actually a general problem with lists and components. You can read more about how to manage lists in a later guide, but we wanted to point out that the devtools can already helps us identify possible issues with the application.
