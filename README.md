# React Native useCallback Stale Closure Bug

This repository demonstrates a common, yet subtle, bug in React Native applications when using the `useCallback` hook with functions that depend on state variables.  The problem arises when the dependency array of `useCallback` is incorrect, resulting in stale closures and unexpected behavior.

## Bug Description
The provided `MyComponent` uses `useState` for `count` and `name`. The `myFunction` is created using `useCallback` with an empty dependency array.  This means the function will only be created once.  If `count` or `name` change, `myFunction` will still use the initial values of `count` and `name`, resulting in stale closures.

## Solution
The solution involves correctly specifying the dependencies in the `useCallback`'s dependency array. If `myFunction` depends on `count` and `name`, then these state variables must be included in the dependency array.