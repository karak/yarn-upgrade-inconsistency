TypeScript errors are introduced by a package manager.

This project depends on 2 packages as @types/react and @types/react-dom -- very trivial.

Run as followings:

```
yarn
npm test
```

you would meet errors like this:

```
node_modules/@types/react-dom/node_modules/@types/react/index.d.ts(3467,13): error TS2403: Subsequent variable declarations must have the same type.  Variable 'a' must be of type 'DetailedHTMLProps<AnchorHTMLAttri
```

It claims the dupulicate type definitions because @types/react itself and dependent one of @types/react-dom are incompatible.

The reason is version inconsistency.

`yarn` assigns '16.0.7' to the former and '16.0.10' to the latter while the package.json of this project requires just '^16.0.7'.

Why yarn keep the version of child-dependent package same as dependent package?

Note it usually occurs after `yarn upgrade`, which never upgrade child dependency.
