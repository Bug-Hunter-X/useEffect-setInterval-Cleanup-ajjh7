# Incorrect Closure Usage in useEffect with setInterval

This example demonstrates a common mistake when using the `useEffect` hook with `setInterval` in React.  The problem arises from how closures work in JavaScript. If the closure captures the state value, it may not reflect the latest state when `setInterval` updates.

## The Bug
The original code uses a closure within the `useEffect` hook that directly accesses the `count` variable. This means that the interval callback always uses the initial value of `count` (which is 0) because of the closure that was created, it does not update to the current value.  As a result, the counter does not increment correctly.

## Solution
The solution is to ensure that the `setInterval` callback always has access to the latest state by using a functional update with `setCount`. The functional update takes the previous state value as an argument and returns the new state value. This ensures that the interval always uses the most recent value.