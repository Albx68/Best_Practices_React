# React Best Practices

## 1. Component Structure & Reusability

- **Break Components Down**: Divide the UI into small, reusable components. Follow the single-responsibility principle, where each component does one thing well.

## 2. State Management

- **Use Hooks Effectively**: use hooks sparingly, you don't need hooks for most cases, only use state for updating UI. Keep the state at the most appropriate level of your app.

| Good Example                         | Bad Example                                     |
| ------------------------------------ | ----------------------------------------------- |
| const [count,setCount] = useState(0) | const [count,setCount] = useState(0)            |
| const countX2 = count\*2             | const [countX2,setCountX2] = useState(count\*2) |

- **Avoid useEffect**:useEffect should only be used for side effects outside of react, you don't need it for updating UI/state.

- 🤢❌
  useEffect(()=>{
  setCountX2(count\*2)
  },[count])

- instead of this, just do const countX2 = count\*2 ✅, you don't need to create a subscription to the state. or even a new state

- **Avoid Prop Drilling**: If props need to pass through many levels, consider using `Context API` or a state management library like `Zustand`.

## 3. Component Naming and Organization

- **File Structure**: Use consistent file and folder structure. Organize components by feature or page to keep things scalable.
- **Naming Conventions**: Name components in PascalCase (e.g., `UserProfile`), and files should match component names.
- **Component Hierarchy**: Follow a logical hierarchy for components, grouping related components together.
- **Component Composition**: Use composition to build complex components from simpler ones. This promotes reusability and maintainability.
- **Component Naming**: Use descriptive names for components that clearly communicate their purpose and functionality. Avoid generic names like `Item` or `Component`. Avoid numbering components. E.g.Form1, Form2 doesn't clearly signify the purpose of the form, in case you want multiple forms, it can be something like KneePainForm, AllurionForm etc.

## 4. Performance Optimization

- **Memoization**: Use `React.memo`, `useMemo`, and `useCallback` to prevent unnecessary re-renders and computations however use them sparingly (refer #2). Avoid Premature Optimization. Only optimize when necessary.
- **Lazy Loading**: Split code and use `React.lazy` and `Suspense` for lazy loading components to improve performance.

## 5. Error Handling

- **Use Error Boundaries**: Add error boundaries at important levels of your app to catch runtime errors.
- **Error Messages**: Provide clear and concise error messages to users. Avoid generic error messages like "Something went wrong."
- **Graceful Failures**: Ensure APIs or components handle failures gracefully with fallbacks or loaders.

## 6. Code Quality

- **Follow Linting Rules**: Don't ignore linting rules. I'll add in proper linting rules, make sure to follow them. Let's use similar IDE configs throught the team.
- \*\*Types: Make sure everything is typed, you can put types in a separate file and import them or localize them to the component that needs them. If the types are going to be reused define them in a separate file.
- **Utility Functions**: Whenever you find yourself writing the same code in multiple places, extract it into a reusable utility function. Put them in a separate file and import them.
- **God Components**: Avoid creating God Components. They are components that have too many responsibilities and are difficult to test. Instead, break down the component into smaller, more focused components. A component should ideally be under 150 Lines Max, less is more, make sure cognitive complexity is relatively low.
- **Constants**: Put all constants in a separate file and import them. This makes it easier to find and maintain.

## 7. Dependencies

- **Regular Updates**: Ensure that project dependencies are regularly updated, but ensure to test after updating.
- **New Dependencies**: Only add new dependencies when necessary and with a clear reason. Make sure you discuss the dependency with the team and get their approval before adding it.

## 8. Pull Requests

- **Pull Requests**: Create pull requests for small, focused changes. This makes it easier to review and merge changes.
- **Commit Messages**: Write clear and concise commit messages that describe the changes made in the commit.
- **Code Reviews**: Request code reviews from other team members or the project owner to ensure code quality and consistency.
