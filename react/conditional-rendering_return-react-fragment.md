# Conditional Rendering in React
## Problem: Returning early a `React Fragment` instead of `null`

### tl;dr

While returning a `React.Fragment` instead of `null` in a React component was a workaround for TypeScript limitations in 2016, this is no longer necessary. Returning `null` is more efficient, makes the code more readable, is officially supported, and aligns with current best practices.

### Code Example

```tsx
const MyComponent = ({ variable }: { variable: boolean }) => {
  if (!variable) {
    return <></>
  }
  
  return (
    <span>Hello</span>
  )
}
```

## Official docs

There is no info about it in [the official docs](https://react.dev/learn/conditional-rendering#conditionally-returning-nothing-with-null). The officially recommended way is to return a `null`.

## Downside

1. Lack of official documentation support: The practice of returning a `React.Fragment` instead of `null` is not covered in the official React documentation.
2. Performance impact: Returning `React.Fragment` involves creating an object of type `fragment`, which requires additional processing by React. In contrast, `null` is a primitive value representing 'nothing,' thus requiring no extra overhead.
3. Code clarity: Using `null` clearly communicates the intention that the component should render nothing, making the code more readable and maintainable.

## Historical context

The practice of returning a `React.Fragment` instead of `null` likely originated around 2016 when TypeScript had limitations in handling `null` as a return type from React components. At that time, returning a `React.Fragment` was a workaround to avoid TypeScript errors. However, this issue has since been resolved, and modern TypeScript fully supports `null` as a valid return type in React components.

## Conclusion

For clarity, performance, and maintainability, it is recommended to use `null` when a React component should render nothing. This approach is supported by the official React documentation and aligns with current best practices of 2024.

## References

https://github.com/microsoft/TypeScript/issues/11566

https://react.dev/learn/conditional-rendering#conditionally-returning-nothing-with-null
