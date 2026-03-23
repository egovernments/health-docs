# DIGIT Frontend React 19 Upgrade

## Overview <a href="#overview" id="overview"></a>

This page provides a comprehensive guide for the major upgrade of the DIGIT Frontend Health Micro-UI application. The upgrade covers multiple significant changes, including React version, build system, routing, and data fetching libraries.

#### Upgrade Summary Table

| Library/Tool     | Before                          | After                         |
| ---------------- | ------------------------------- | ----------------------------- |
| React            | 17.0.2                          | 19.0.0                        |
| React DOM        | 17.0.2                          | 19.0.0                        |
| React Router DOM | 5.3.0                           | 6.25.1                        |
| React Query      | 3.6.1                           | @tanstack/react-query 5.62.16 |
| React Hook Form  | 6.15.8                          | 7.52.2                        |
| React i18next    | 11.16.2                         | 15.0.0                        |
| React Redux      | 7.x                             | 9.2.0                         |
| Build System     | microbundle-crl / react-scripts | Webpack 5                     |

***

## Migration Summary <a href="#migration-summary" id="migration-summary"></a>

#### What Changed

1. **Build System:** Migrated from `microbundle-crl` and `react-scripts` to a custom **Webpack 5** configuration
2. **React Version:** Major upgrade from **React 17** to **React 19** (skipping React 18)
3. **Routing:** Complete rewrite from **React Router v5** to **v6** syntax
4. **Data Fetching:** Migration from **react-query v3** to **@tanstack/react-query v5**
5. **Form Handling:** Updated **react-hook-form** from v6 to v7
6. **Internationalization:** Updated **react-i18next** from v11 to v15

***

## Build System Migration <a href="#build-system" id="build-system"></a>

#### From microbundle-crl to Webpack 5

**Why the Change?**

* Better control over build configuration
* Improved hot module replacement (HMR)
* Better code splitting and optimisation
* Custom proxy configuration for development
* Bundle analysis capabilities

**Old Setup (microbundle-crl)**

```
{
  "scripts": {
    "start": "microbundle-crl watch --no-compress --format modern,cjs",
    "build": "microbundle-crl --compress --no-sourcemap --format cjs"
  }
}
```

**New Setup (Webpack 5)**

```
{
  "devDependencies": {
    "webpack": "^5.97.1",
    "webpack-cli": "^6.0.1",
    "webpack-dev-server": "^5.2.0",
    "webpack-merge": "^5.10.0",
    "html-webpack-plugin": "^5.6.3",
    "clean-webpack-plugin": "^4.0.0",
    "terser-webpack-plugin": "^5.3.10",
    "compression-webpack-plugin": "^11.1.0"
  },
  "scripts": {
    "start": "node start-dev.js",
    "start:webpack-only": "webpack serve --config webpack.dev.js --port 3000",
    "build": "npm run build:packages && webpack --config webpack.prod.js",
    "build:analyse": "ANALYZE=true webpack --config webpack.prod.js"
  }
}
```

**Webpack Configuration Structure**

```
project/
├── webpack.common.js    # Shared configuration
├── webpack.dev.js       # Development configuration
├── webpack.prod.js      # Production configuration
└── start-dev.js         # Development server startup script
```

***

## React 17 to React 19 Migration <a href="#react-migration" id="react-migration"></a>

### Breaking Changes

#### **1. Rendering API (Critical)**

**React 17 (Before)**

```
import ReactDOM from 'react-dom';

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
```

**React 19 (After)**

```
import { createRoot } from 'react-dom/client';

const container = document.getElementById('root');
const root = createRoot(container);

root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

#### **2. forwardRef Removal**

**React 17 (Before)**

```
const CustomInput = React.forwardRef((props, ref) => {
  return <input ref={ref} {...props} />;
});
```

**React 19 (After)**

```
function CustomInput({ ref, ...props }) {
  return <input ref={ref} {...props} />;
}
```

#### **3. Context Provider Syntax**

**React 17 (Before)**

```
<ThemeContext.Provider value={theme}>
  {children}
</ThemeContext.Provider>
```

**React 19 (After)**

```
<ThemeContext value={theme}>
  {children}
</ThemeContext>
```

#### **4. defaultProps Removed**

**React 17 (Before)**

```
function Button({ color }) { ... }
Button.defaultProps = { color: 'blue' };
```

**React 19 (After)**

```
function Button({ color = 'blue' }) { ... }
// Use default parameters
```

#### **5. Automatic Batching**

{% hint style="info" %}
**Note:** React 19 automatically batches all state updates, even in setTimeout, promises, and native event handlers.
{% endhint %}

```
// React 17: Multiple re-renders in setTimeout/promises
// React 19: Single batched re-render
setTimeout(() => {
  setCount(c => c + 1);
  setFlag(f => !f);
  setName('React');
  // All three updates batched into one re-render
}, 1000);
```

#### **6. New Hooks in React 19**

```
// useActionState - for form actions
const [state, action, isPending] = useActionState(submitForm, initialState);

// useOptimistic - for optimistic updates
const [optimisticItems, addOptimistic] = useOptimistic(items);

// useFormStatus - for form submission status
function SubmitButton() {
  const { pending } = useFormStatus();
  return <button disabled={pending}>Submit</button>;
}

// use() - for reading resources in render
const data = use(fetchData());
```

***

## React Router v5 to v6 Migration <a href="#router-migration" id="router-migration"></a>

### Major Syntax Changes

#### **1. Switch → Routes**

**v5 (Before)**

```
import { Switch, Route } from 'react-router-dom';

<Switch>
  <Route exact path="/">
    <Home />
  </Route>
  <Route path="/about">
    <About />
  </Route>
</Switch>
```

**v6 (After)**

```
import { Routes, Route } from 'react-router-dom';

<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about" element={<About />} />
</Routes>
```

#### **2. useHistory → useNavigate**

**v5 (Before)**

```
import { useHistory } from 'react-router-dom';

function Component() {
  const history = useHistory();

  const handleClick = () => {
    history.push('/home');
    history.replace('/login');
    history.goBack();
  };
}
```

**v6 (After)**

```
import { useNavigate } from 'react-router-dom';

function Component() {
  const navigate = useNavigate();

  const handleClick = () => {
    navigate('/home');
    navigate('/login', { replace: true });
    navigate(-1);
  };
}
```

#### **3. Redirect → Navigate**

**v5 (Before)**

```
import { Redirect } from 'react-router-dom';

<Redirect to="/login" />
<Redirect from="/old" to="/new" />
```

**v6 (After)**

```
import { Navigate } from 'react-router-dom';

<Navigate to="/login" />
<Navigate to="/new" replace />
```

#### **4. Route Props → Hooks**

**v5 (Before)**

```
// Route passes match, location, history as props
<Route path="/users/:id" component={UserProfile} />

function UserProfile({ match, location, history }) {
  const { id } = match.params;
}
```

**v6 (After)**

```
// Use hooks instead
<Route path="/users/:id" element={<UserProfile />} />

function UserProfile() {
  const { id } = useParams();
  const location = useLocation();
  const navigate = useNavigate();
}
```

#### **5. Nested Routes**

**v5 (Before)**

```
// Parent component
<Route path="/dashboard" component={Dashboard} />

// Dashboard component
function Dashboard({ match }) {
  return (
    <div>
      <Route path={`${match.path}/settings`}
             component={Settings} />
    </div>
  );
}
```

**v6 (After)**

```
// Define all routes together
<Routes>
  <Route path="/dashboard" element={<Dashboard />}>
    <Route path="settings" element={<Settings />} />
  </Route>
</Routes>

// Dashboard component uses Outlet
import { Outlet } from 'react-router-dom';

function Dashboard() {
  return <div><Outlet /></div>;
}
```

#### **6. NavLink Changes**

**v5 (Before)**

```
<NavLink
  to="/home"
  activeClassName="active"
  activeStyle={{ color: 'red' }}>
  Home
</NavLink>
```

**v6 (After)**

```
<NavLink
  to="/home"
  className={({ isActive }) =>
    isActive ? 'active' : ''}
  style={({ isActive }) =>
    ({ color: isActive ? 'red' : 'inherit' })}>
  Home
</NavLink>
```

#### Quick Reference Table

<table><thead><tr><th width="310.73046875">v5</th><th>v6</th></tr></thead><tbody><tr><td><code>&#x3C;Switch></code></td><td><code>&#x3C;Routes></code></td></tr><tr><td><code>&#x3C;Route component={X}></code></td><td><code>&#x3C;Route element={&#x3C;X />}></code></td></tr><tr><td><code>&#x3C;Route render={() => ...}></code></td><td><code>&#x3C;Route element={...}></code></td></tr><tr><td><code>&#x3C;Redirect to="/"></code></td><td><code>&#x3C;Navigate to="/" replace></code></td></tr><tr><td><code>useHistory()</code></td><td><code>useNavigate()</code></td></tr><tr><td><code>history.push(path)</code></td><td><code>navigate(path)</code></td></tr><tr><td><code>history.replace(path)</code></td><td><code>navigate(path, { replace: true })</code></td></tr><tr><td><code>history.goBack()</code></td><td><code>navigate(-1)</code></td></tr><tr><td><code>useRouteMatch()</code></td><td><code>useMatch()</code></td></tr><tr><td><code>match.params</code></td><td><code>useParams()</code></td></tr></tbody></table>

***

## React Query to TanStack Query v5 Migration <a href="#query-migration" id="query-migration"></a>

#### Package Change

**Old (v3)**

```
npm install react-query@3.6.1
```

**New (v5)**

```
npm install @tanstack/react-query@5.62.16
```

### Import Changes

**v3 (Before)**

```
import {
  useQuery,
  useMutation,
  QueryClient,
  QueryClientProvider
} from 'react-query';
```

**v5 (After)**

```
import {
  useQuery,
  useMutation,
  QueryClient,
  QueryClientProvider
} from '@tanstack/react-query';
```

#### **1. useQuery Signature Change**

**v3 (Before)**

```
// Key and function as separate arguments
const { data, isLoading, error } = useQuery(
  'todos',
  fetchTodos,
  { staleTime: 5000 }
);

// With variables
const { data } = useQuery(
  ['todo', todoId],
  () => fetchTodoById(todoId)
);
```

**v5 (After)**

```
// Single object argument
const { data, isPending, error } = useQuery({
  queryKey: ['todos'],
  queryFn: fetchTodos,
  staleTime: 5000
});

// With variables
const { data } = useQuery({
  queryKey: ['todo', todoId],
  queryFn: () => fetchTodoById(todoId)
});
```

#### **2. useMutation Signature Change**

**v3 (Before)**

```
const mutation = useMutation(createTodo, {
  onSuccess: () => {
    queryClient.invalidateQueries('todos');
  }
});
```

**v5 (After)**

```
const mutation = useMutation({
  mutationFn: createTodo,
  onSuccess: () => {
    queryClient.invalidateQueries({
      queryKey: ['todos']
    });
  }
});
```

#### **3. Status Flags Renamed**

**Important:** `isLoading` is now `isPending`

**v3 (Before)**

```
const {
  isLoading,
  isError,
  isSuccess,
  isIdle
} = useQuery(...);
```

**v5 (After)**

```
const {
  isPending,  // was isLoading
  isError,
  isSuccess
} = useQuery(...);
// isIdle is removed
```

#### **4. Query Invalidation**

**v3 (Before)**

```
queryClient.invalidateQueries('todos');
queryClient.invalidateQueries(['todos', 1]);
```

**v5 (After)**

```
queryClient.invalidateQueries({ queryKey: ['todos'] });
queryClient.invalidateQueries({ queryKey: ['todos', 1] });
```

#### Quick Reference Table

<table><thead><tr><th width="284.98828125">v3</th><th>v5</th></tr></thead><tbody><tr><td><code>useQuery(key, fn, options)</code></td><td><code>useQuery({ queryKey, queryFn, ...options })</code></td></tr><tr><td><code>useMutation(fn, options)</code></td><td><code>useMutation({ mutationFn, ...options })</code></td></tr><tr><td><code>isLoading</code></td><td><code>isPending</code></td></tr><tr><td><code>isIdle</code></td><td>Check <code>status === 'pending' &#x26;&#x26; fetchStatus === 'idle'</code></td></tr><tr><td><code>invalidateQueries('key')</code></td><td><code>invalidateQueries({ queryKey: ['key'] })</code></td></tr><tr><td><code>refetchQueries('key')</code></td><td><code>refetchQueries({ queryKey: ['key'] })</code></td></tr><tr><td><code>setQueryData('key', data)</code></td><td><code>setQueryData(['key'], data)</code></td></tr></tbody></table>

***

## Other Library Updates <a href="#other-libraries" id="other-libraries"></a>

#### React Hook Form (v6 → v7)

**Register Method Change**

**v6 (Before)**

```
<input
  name="email"
  ref={register({ required: true })}
/>
```

**v7 (After)**

```
<input
  {...register('email', { required: true })}
/>
```

#### React i18next (v11 → v15)

```
// Same API, improved TypeScript support
import { useTranslation } from 'react-i18next';
const { t, i18n } = useTranslation();
```

#### React Redux (v7 → v9)

* Better React 19 compatibility
* Improved TypeScript support
* Same `useSelector` and `useDispatch` API

***

## Challenges Faced <a href="#challenges" id="challenges"></a>

#### 1. Peer Dependency Conflicts

**Problem:** Multiple libraries had peer dependencies on different React versions.

**Solution:** Use resolutions in package.json

```
{
  "resolutions": {
    "**/react": "19.0.0",
    "**/react-dom": "19.0.0",
    "**/react-query": "@tanstack/react-query@^5.62.16"
  }
}
```

#### 2. Build System Complexity

**Problem:** microbundle-crl didn't support the advanced features needed.

**Solution:** Custom Webpack 5 configuration with proper code splitting and HMR.

#### 3. React Router Complete Rewrite

**Problem:** v5 to v6 required rewriting all routing logic.

**Solution:** Systematic migration using the reference tables in this document.

#### 4. React Query Breaking Changes

**Problem:** Complete API signature change from v3 to v5.

**Solution:** Search and replace using regex patterns, then manual review.

#### 5. forwardRef Throughout Codebase

**Problem:** Many components used the forwardRef pattern.

**Solution:** Convert all forwardRef to ref as a prop pattern.

#### 6. Automatic Batching Side Effects

**Problem:** Code that relied on synchronous state updates broke.

**Solution:** Use `flushSync` for critical synchronous updates:

```
import { flushSync } from 'react-dom';

setTimeout(() => {
  flushSync(() => {
    setLoading(true);
  });
  // DOM is now updated
  fetchData();
  setLoading(false);
}, 100);
```

***

## Troubleshooting Guide <a href="#troubleshooting" id="troubleshooting"></a>

#### Error: "ReactDOM.render is no longer supported"

```
// Fix: Update entry point
import { createRoot } from 'react-dom/client';
createRoot(document.getElementById('root')).render(<App />);
```

#### Error: "useHistory is not exported"

```
// Fix: Use useNavigate instead
import { useNavigate } from 'react-router-dom';
const navigate = useNavigate();
navigate('/path');
```

#### Error: "Switch is not exported"

```
// Fix: Use Routes instead
import { Routes, Route } from 'react-router-dom';
<Routes>
  <Route path="/" element={<Home />} />
</Routes>
```

#### Error: "useQuery expects object"

```
// Fix: Use object syntax
useQuery({
  queryKey: ['key'],
  queryFn: fetchFunction
});
```

#### Error: "isLoading is undefined"

```
// Fix: Use isPending instead
const { isPending } = useQuery({ ... });
```

#### Peer Dependency Warnings

```
# Use resolutions in package.json or
npm install --legacy-peer-deps
```

#### Webpack Build Fails

```
# Clear cache and reinstall
rm -rf node_modules
rm package-lock.json
npm install
```

***

## Upgrade Roadmap <a href="#roadmap" id="roadmap"></a>

**Phase 1: Preparation**

* Create a feature branch for the upgrade
* Audit all dependencies and their React 19 compatibility
* Document current application behaviour
* Set up comprehensive test coverage
* Back up the current configuration

**Phase 2: Build System Migration**

* Create webpack.common.js
* Create webpack.dev.js
* Create webpack.prod.js
* Configure Babel for React 19
* Set up development server with proxy
* Configure code splitting and optimization
* Test build process

**Phase 3: Core Dependencies Update**

* Update React and React DOM to 19.0.0
* Update entry point to use createRoot
* Add resolutions for React version
* Fix initial compilation errors
* Test basic rendering

**Phase 4: React Router Migration**

* Update react-router-dom to v6
* Replace Switch with Routes
* Replace the Route component prop with the element
* Replace Redirect with Navigate
* Replace useHistory with useNavigate
* Update nested routes to use Outlet
* Update NavLink syntax
* Test all navigation flows

**Phase 5: React Query Migration**

* Install @tanstack/react-query v5
* Update all imports
* Convert useQuery to object syntax
* Convert useMutation to object syntax
* Update invalidateQueries calls
* Replace isLoading with isPending
* Test all data fetching

**Phase 6: Other Libraries**

* Update react-hook-form to v7
* Update register syntax
* Update react-i18next
* Update react-redux
* Update other dependencies

**Phase 7: Component Updates**

* Remove forwardRef usage
* Update defaultProps to default parameters
* Update Context.Provider syntax
* Add proper cleanup to useEffect hooks
* Fix any batching-related issues

**Phase 8: Testing & QA**

* Run full test suite
* Fix failing tests
* Manual testing of all features
* Performance profiling
* Browser compatibility testing
* Fix any remaining issues

**Phase 9: Deployment**

* Code review
* Staging deployment
* Production deployment
* Monitor for errors
* Update documentation

***

## References

* [React 19 Upgrade Guide](https://react.dev/blog/2024/04/25/react-19-upgrade-guide)
* [React Router v6 Upgrade Guide](https://reactrouter.com/en/main/upgrading/v5)
* [TanStack Query v5 Migration Guide](https://tanstack.com/query/latest/docs/framework/react/guides/migrating-to-v5)
* [React Hook Form Migration Guide](https://react-hook-form.com/migrate-v6-to-v7)
* [Webpack 5 Documentation](https://webpack.js.org/)
