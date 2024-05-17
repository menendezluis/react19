# React Upcoming Features and Improvements

## New Compiler

React is working on implementing a new compiler. Currently, this technology is being implemented on Instagram and will be released in future versions of React.

## Server Components

Third-party frameworks will no longer be necessary as they will be part of React itself.

## Actions

A NEW way to interact with the DOM.

## Document Metadata

An upcoming improvement, giving developers the power to do more with less code.

## Assets Loading

Allows loading assets behind the scenes, which can improve application load times and user experience.

## Web Components

They will now be part of React.

## Better Hooks

Many are being removed and new players are being brought to the table.

## Issues Being Addressed

- Excessive render problems.
- Difficulties managing renders during development.
- Complex memory handling causing confusion among novice programmers (`useMemo`, `useCallback`, `memo`).

## How They Aim to Improve It

- Render management will be handled AUTOMATICALLY by React.
- Manual hooks for memory management will no longer be necessary.

## Let's Dive Into the Details

### New Compiler

The current compiler leaves MUCH to be desired, from bad practices to making developers prone to implementing them using hooks like `useMemo`, `useCallback`, `memo`, etc., which SHOULD ALREADY be part of the library itself. After many years, they have finally listened to the developers' cries and decided that this management will be done AUTOMATICALLY. The library itself will decide how and when a state change occurs and with it a render.

So, goodbye `useMemo()`, goodbye `useCallback()`, and goodbye `memo`.

Again, as mentioned earlier, these new changes are being tested directly on their own products, starting with Instagram before being made public.

### Server Components

Third-party frameworks will no longer be necessary as they will be part of React. One of the qualities that made everyone prefer using NextJs will now be directly in the library itself. NextJs initially implemented this idea, and by version 13, it became the default. If you've coded with this framework, you know that to indicate a component is rendered on the client, you use the directive `use client`. All this will now be part of React but in reverse; by default, client-rendered components will be used, and if we want to use Server Components, we'll need to use `use server`.

#### Improvements:

- **SEO:** Increases web vitals scores, which can improve the overall application rating and thus better search engine ranking.
- **Performance Improvement:** Related to SEO improvements, as one of the most important web vitals is initial load speed. The use of Server Components brings a VERY fast initial load, benefiting heavier applications.
- **Server-Side Execution:** We can now execute code on the server side since it is necessary to set up a server to implement these components.

### Actions

Actions are used with server components and allow calling server functions that mutate data. In the browser, the traditional HTML `form` element is the way to submit these mutations, so now React provides server actions for them.

### Web Components

Web Components are a way to implement components purely composed of HTML, CSS, and JS, allowing them to be incorporated agnostically into any project, regardless of the front-end technology used.

Currently, incorporating such components into a React project is not straightforward, requiring transforming the Web Component into a React one, installing a library to solve the issue, or writing additional code. In version 19, this will no longer be a problem as they can now be used without conversion.

### Document Metadata

In SEO, elements like "meta tags," "title," "link tags," etc., are used to identify different concepts of our application to search engines and determine if it will be useful to meet users' information needs. To properly manage these elements across different routes, extra code or third-party libraries were needed. As I always say, the less we code and the fewer third-party codes we have... the better. Now we have our own tags like `<title>`, etc.

### Assets Loading

To avoid struggling with web vitals issues like "INP" (Interaction to Next Paint), one strategy is to render the most important content first and then load the rest behind the scenes without the user noticing. This way, the initial load is fast, and the user can interact with the page. Now, "preload" and "preinit" APIs can be used, providing better control over resources that need to be loaded and initialized.

### New Hooks

As mentioned earlier, goodbye `useMemo`, goodbye `useCallback`, goodbye `forwardRef`, and goodbye `memo`, but that doesn't mean there won't be new hooks!

#### `use()`

Used with promises, asynchronous code, and context.

```
const value = use(fetchData());
```

We no longer need to use useContext(), now use(YourContext) is directly used.

useFormStatus()
Provides information about the submit status of a form.

```
const { pending, data, method, action } = useFormStatus();
// or
const { status } = useFormStatus();
```

VERY similar to react-hook-form.

useActionState()
Replaces the previously named useFormState() as the original intention was different from what developers understood. Before, we thought it only allowed updating the form state according to the submit result.

```
const [state, formAction] = useFormState(fn, initialState, permalink?);
```

But it is much more than that; the main idea was to wrap the action's state used in the hook, returning an action that can be tracked to get the last value returned by that action. Thus, we see that useFormState doesn't even need to be used in a form!

The changes now are:

The name changes to useActionState
A "pending" state is added
Imported from the "react" library, not from "react-dom"

```
const [state, action, isPending] = useActionState(formAction);
```

useOptimistic()
Allows showing a different state while asynchronous logic is being executed.

```
const [optimisticMessage, addOptimisticMessage] = useOptimistic(state, updatefn);
```

The main idea is that while waiting for the response of an asynchronous call, an "optimistic" state can be shown so the user gets an immediate response. Once we have the real response, we show the result of the call.

It's called "optimistic" because it assumes the result was satisfactory even though we don't know it yet.

How to Upgrade to React 19
First of all, you should know that it is NOT RECOMMENDED to use React 19 for production applications as all these changes are still in testing and may change, besides possibly presenting issues.

To upgrade your project to React 19, you just need to do:

```

# replace pnpm with your preferred package manager
pnpm upgrade react@canary react-dom@canary

# in case of npm
npm update react@canary react-dom@canary


```
# react19
