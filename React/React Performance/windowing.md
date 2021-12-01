### Windowing/ Virtualization 

Windowing or Virtualization of lists is a technique to load the items which will be displayed at the viewport.Load the rest when they encountered while scrolling.
Suppose your list has 10000 items and you have to display only 10 items at the screen.Loading 10000 items will be an issue for the performance.So instead of 10000 we will only load 10 items and as the user start scrolling we will start loading the rest.


We have many libraries in react
1. react-window [github](https://github.com/bvaughn/react-window) [npm](https://www.npmjs.com/package/react-window) [docs](https://react-window.vercel.app/#/examples/list/fixed-size)
2. react-virtualized [github](https://github.com/bvaughn/react-virtualized) [npm](https://www.npmjs.com/package/react-virtualized) [docs](http://bvaughn.github.io/react-virtualized/#/components/List)
3. react-virtual [github](https://github.com/tannerlinsley/react-virtual) [docs](https://react-virtual.tanstack.com/)

You can read about more from 👎
[Web.dev Virtualization in React](https://web.dev/virtualize-long-lists-react-window/)
