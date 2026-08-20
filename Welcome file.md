---


---




  
  <title>MERN &amp; React Native Complete Technical Interview Guide</title>
  


  <div class="header-card">
    <h2>Full-Stack Technical Interview Master Guide</h2>
    <p><strong>Candidate:</strong> Jayesh Kumar Dhariyal | <strong>Target Role:</strong> Software Developer (Full-Stack / Mobile)</p>
    <p><strong>Company:</strong> Virtual Wallet Systems Pvt. Ltd. (ImWallet) | <strong>Stack:</strong> React.js, Node.js, Express, MongoDB, React Native</p>
  </div>
  <h1>1. JavaScript Core &amp; ES6+ (The Foundation)</h1>
  <div class="qa-block">
    <span class="q-title">1. var vs let vs const:</span>
    <code>var</code> is function-scoped and hoisted with <code>undefined</code>. <code>let</code> and <code>const</code> are block-scoped and hoisted into a Temporal Dead Zone (TDZ). <code>const</code> prevents variable reassignment.
  </div>
  <div class="qa-block">
    <span class="q-title">2. Data Types &amp; Equality:</span>
    Primitives: <code>string</code>, <code>number</code>, <code>bigint</code>, <code>boolean</code>, <code>undefined</code>, <code>symbol</code>, <code>null</code>. Non-Primitives: <code>Object</code>, <code>Array</code>, <code>Function</code>.<br>
    <code>==</code> performs type coercion before comparison; <code>===</code> checks both value and data type strictly without type coercion.
  </div>
  <div class="qa-block">
    <span class="q-title">3. Hoisting &amp; Closures:</span>
    <strong>Hoisting:</strong> Variable/function declarations are evaluated at top of scope before execution. Functions hoist with body; <code>var</code> hoists as <code>undefined</code>.<br>
    <strong>Closure:</strong> A function bundled with its lexical environment, allowing inner functions to retain access to outer variables even after the outer function finishes executing.
<pre><code>function createWallet(initialBalance) {
  let balance = initialBalance;
  return {
    addMoney: (amt) =&gt; { balance += amt; return balance; },
    getBalance: () =&gt; balance
  };
}</code></pre>
  </div>
  <div class="qa-block">
    <span class="q-title">4. Shallow Copy vs Deep Copy:</span>
    <strong>Shallow Copy</strong> (<code>{...obj}</code>, <code>Object.assign()</code>) only duplicates top-level references; nested objects remain linked. <strong>Deep Copy</strong> (<code>structuredClone(obj)</code> or <code>JSON.parse(JSON.stringify(obj))</code>) recursively duplicates all nested layers.
  </div>
  <div class="qa-block">
    <span class="q-title">5. call(), apply(), bind(), and 'this':</span>
    <code>this</code> points to the object executing the function. In arrow functions, <code>this</code> is lexically inherited from enclosing scope.
    <ul>
      <li><code>fn.call(ctx, arg1, arg2)</code>: Invokes immediately with comma-separated arguments.</li>
      <li><code>fn.apply(ctx, [args])</code>: Invokes immediately with an array of arguments.</li>
      <li><code>fn.bind(ctx, arg1)</code>: Returns a new function with bound context to invoke later.</li>
    </ul>
  </div>
  <div class="qa-block">
    <span class="q-title">6. Higher-Order Array Functions (map, filter, reduce):</span>
    <code>map()</code> transforms elements into a new array. <code>filter()</code> returns elements passing a condition. <code>reduce()</code> accumulates items into a single final value.
<pre><code>const txns = [100, 250, 450];
const total = txns.reduce((acc, curr) =&gt; acc + curr, 0); // 800</code></pre>
  </div>
  <div class="qa-block">
    <span class="q-title">7. Event Loop &amp; Asynchronous JavaScript:</span>
    JS is single-threaded. The <strong>Event Loop</strong> monitors the Call Stack. When clear, it processes the <strong>Microtask Queue</strong> (Promises, <code>async/await</code> handlers) first, followed by the <strong>Macrotask Queue</strong> (<code>setTimeout</code>, I/O events).
  </div>
  <h1>2. React.js Complete 50 Q&amp;A Breakdown</h1>
  <h2>Section A: Architecture, Virtual DOM &amp; JSX</h2>
  <div class="qa-block"><span class="q-title">1. What is React?</span> A component-based JavaScript library for building fast, interactive user interfaces by breaking UI into small, reusable pieces.</div>
  <div class="qa-block"><span class="q-title">2. Why created?</span> Created by Facebook (2011–2013) to solve DOM manipulation slowness (like jQuery) in large-scale apps with fast, predictable state updates.</div>
  <div class="qa-block"><span class="q-title">3. Key Features:</span> JSX, Virtual DOM, Component architecture, Unidirectional data flow, Hooks, and React Router.</div>
  <div class="qa-block"><span class="q-title">4. What is JSX?</span> JavaScript XML—allows writing HTML-like syntax inside JS, compiled via Babel into <code>React.createElement()</code>.</div>
  <div class="qa-block"><span class="q-title">5. Virtual DOM:</span> In-memory lightweight representation of the real DOM.</div>
  <div class="qa-block"><span class="q-title">6. Efficient DOM Updates:</span> State change $\rightarrow$ New Virtual DOM created $\rightarrow$ Diffing algorithm compares against old VDOM $\rightarrow$ Reconciliation calculates minimal changes $\rightarrow$ Real DOM is patched in batches.</div>
  <div class="qa-block"><span class="q-title">7. Real DOM vs Virtual DOM:</span> Real DOM re-renders whole trees causing layout reflows; Virtual DOM updates in-memory and patches only changed nodes.</div>
  <h2>Section B: Components, Props &amp; State</h2>
  <div class="qa-block"><span class="q-title">8. Components:</span> Independent, reusable UI units returning JSX. Functional and Class components.</div>
  <div class="qa-block"><span class="q-title">9. Functional vs Class:</span> Functional components use Hooks, require less boilerplate, and are the modern standard. Class components use <code>this.state</code> and lifecycle methods.</div>
  <div class="qa-block"><span class="q-title">10. Props:</span> Read-only (immutable) parameters passed downward from parent to child to configure components.</div>
  <div class="qa-block"><span class="q-title">11. State:</span> Internal mutable data managed inside a component. Updates trigger UI re-renders automatically.</div>
  <div class="qa-block"><span class="q-title">12. Props vs State:</span> Props are passed from outside (read-only); State is maintained locally within the component.</div>
  <h2>Section C: Hooks Mastery</h2>
  <div class="qa-block"><span class="q-title">13. useState:</span> Declares local reactive state: <code>const [count, setCount] = useState(0);</code></div>
  <div class="qa-block"><span class="q-title">14. useEffect:</span> Handles side effects (data fetching, timers, DOM manipulation). Replaces class lifecycle methods.</div>
  <div class="qa-block"><span class="q-title">15. What are Hooks?</span> Functions prefixed with <code>use</code> that enable state and lifecycle features inside functional components.</div>
  <div class="qa-block"><span class="q-title">16. Why Hooks?</span> Eliminates class boilerplate, avoids <code>this</code> binding issues, and makes stateful logic easily extractable/reusable.</div>
  <div class="qa-block"><span class="q-title">17. Dependency Array in useEffect:</span> Controls when the effect executes. Re-runs only when listed variables change.</div>
  <div class="qa-block"><span class="q-title">18. Missing Dependency Array:</span> If omitted, the effect runs after <em>every single render</em>, risking infinite loops. If <code>[]</code>, runs once on mount.</div>
  <div class="qa-block"><span class="q-title">30. useRef:</span> Creates a mutable object (<code>ref.current</code>) that persists across renders without triggering a re-render. Used for DOM access and persisting timer IDs.</div>
  <div class="qa-block"><span class="q-title">31. useRef vs useState:</span> Updating <code>useRef</code> is silent (no re-render); updating <code>useState</code> triggers a component re-render.</div>
  <div class="qa-block"><span class="q-title">32. useMemo:</span> Memoizes the <em>result</em> of an expensive calculation: <code>const val = useMemo(() =&gt; calc(x), [x]);</code></div>
  <div class="qa-block"><span class="q-title">33. useCallback:</span> Memoizes a <em>function definition</em> across renders to keep reference identity intact when passed to memoized children.</div>
  <div class="qa-block"><span class="q-title">39. Custom Hooks:</span> JavaScript functions prefixed with <code>use</code> calling other hooks to share stateful logic across components.</div>
  <h2>Section D: Rendering, Forms &amp; Patterns</h2>
  <div class="qa-block"><span class="q-title">19. Conditional Rendering:</span> Displaying UI conditionally via ternary (<code>cond ? &lt;A/&gt; : &lt;B/&gt;</code>) or <code>&amp;&amp;</code> operators.</div>
  <div class="qa-block"><span class="q-title">20. List Rendering &amp; 21. Key Prop:</span> Render arrays using <code>.map()</code>. Keys provide stable identities so React tracks added, removed, or moved items without rebuilding the whole list.</div>
  <div class="qa-block"><span class="q-title">22. Event Handling:</span> Handled via camelCase (<code>onClick</code>) passing function references wrapped in React's synthetic event system.</div>
  <div class="qa-block"><span class="q-title">23. Two-Way Binding &amp; 24. Controlled Components:</span> Form elements whose value is controlled by React state via <code>value</code> and <code>onChange</code>.</div>
  <div class="qa-block"><span class="q-title">25. Uncontrolled Components:</span> Form elements that store state in the DOM directly, accessed via <code>useRef()</code>.</div>
  <div class="qa-block"><span class="q-title">26. Lifting State Up:</span> Moving state to the nearest common ancestor to share between sibling components.</div>
  <div class="qa-block"><span class="q-title">27. Prop Drilling &amp; 28. Context API:</span> Prop drilling is passing props through unnecessary intermediate layers. Context API provides global state across the tree without manual prop drilling.</div>
  <div class="qa-block"><span class="q-title">29. useContext:</span> Hook allowing functional components to consume context values directly.</div>
  <h2>Section E: Advanced Optimization &amp; Lifecycle</h2>
  <div class="qa-block"><span class="q-title">34. React Fragment:</span> <code>&lt;&gt;...&lt;/&gt;</code> groups elements without creating unnecessary wrapper DOM nodes.</div>
  <div class="qa-block"><span class="q-title">35. React Router:</span> Client-side routing library for single-page applications without full page reloads.</div>
  <div class="qa-block"><span class="q-title">36. SPA vs MPA:</span> SPA loads one HTML page and updates content dynamically via JS; MPA requests full HTML pages from the server on each route.</div>
  <div class="qa-block"><span class="q-title">37. Lazy Loading &amp; 38. Code Splitting:</span> Dynamically loading components on-demand using <code>React.lazy()</code> and <code>Suspense</code> to reduce initial JS bundle size.</div>
  <div class="qa-block"><span class="q-title">40. Lifecycle Phases:</span> <strong>Mounting</strong> (created in DOM), <strong>Updating</strong> (re-rendered on prop/state change), and <strong>Unmounting</strong> (cleanup/removed from DOM).</div>
  <div class="qa-block"><span class="q-title">42. npm vs npx:</span> <code>npm</code> installs packages locally/globally; <code>npx</code> executes binaries directly without persistent installation.</div>
  <div class="qa-block"><span class="q-title">44. Reconciliation:</span> The diffing algorithm comparing old and new VDOM trees to execute minimal DOM updates.</div>
  <div class="qa-block"><span class="q-title">45. BrowserRouter vs HashRouter:</span> <code>BrowserRouter</code> uses standard paths via HTML5 history API (needs server rewrite rules); <code>HashRouter</code> uses URL hashes (<code>#</code>) for static hosting.</div>
  <div class="qa-block"><span class="q-title">47. React.memo vs 48. useMemo:</span> <code>React.memo</code> is a HOC preventing component re-renders if props don't change. <code>useMemo</code> memoizes calculated values inside a component.</div>
  <div class="qa-block"><span class="q-title">49. Strict Mode:</span> Dev-only tool that double-invokes render/effects to uncover unexpected side-effects and deprecated APIs.</div>
  <div class="qa-block"><span class="q-title">50. Higher-Order Component (HOC):</span> A function taking a component and returning an enhanced component with added logic.</div>
  <h1>3. Node.js &amp; Express.js Backend</h1>
  <div class="qa-block">
    <span class="q-title">Architecture:</span> Single-threaded event loop executing on Google Chrome's <strong>V8 Engine</strong> with <strong>libuv</strong> managing thread pools for non-blocking asynchronous file/network I/O.
  </div>
  <div class="qa-block">
    <span class="q-title">Streams vs Buffers:</span> <code>fs.readFile()</code> buffers entire files in memory; <code>fs.createReadStream()</code> streams data in manageable chunks, preventing server crashes during high traffic.
  </div>
  <div class="qa-block">
    <span class="q-title">Express Middleware &amp; Token Verification:</span>
<pre><code>const authMiddleware = (req, res, next) =&gt; {
  const token = req.headers.authorization?.split(" ")[1];
  if (!token) return res.status(401).json({ message: "Unauthorized access" });
  try {
    const decoded = jwt.verify(token, process.env.JWT_SECRET);
    req.user = decoded;
    next();
  } catch (err) {
    res.status(403).json({ message: "Invalid or expired token" });
  }
};</code></pre>
  </div>
  <h1>4. MongoDB &amp; Mongoose Database</h1>
  <table>
    <thead>
      <tr>
        <th>Feature</th>
        <th>Relational Database (SQL)</th>
        <th>MongoDB (NoSQL)</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><strong>Structure</strong></td>
        <td>Fixed tables, rows, columns</td>
        <td>Flexible BSON documents in Collections</td>
      </tr>
      <tr>
        <td><strong>Schema</strong></td>
        <td>Rigid, requires explicit migrations</td>
        <td>Dynamic / Schema-optional</td>
      </tr>
      <tr>
        <td><strong>Relationships</strong></td>
        <td>Foreign Keys &amp; <code>JOIN</code> operations</td>
        <td>Embedded subdocuments or <code>$lookup</code></td>
      </tr>
      <tr>
        <td><strong>Scaling</strong></td>
        <td>Vertical scaling (larger servers)</td>
        <td>Horizontal scaling (Sharding across clusters)</td>
      </tr>
    </tbody>
  </table>
  <div class="qa-block">
    <span class="q-title">Aggregation Pipeline (FinTech Analytics Example):</span>
<pre><code>const txnSummary = await Transaction.aggregate([
  { $match: { status: "SUCCESS", createdAt: { $gte: startOfDay } } },
  { $group: { _id: "$merchantId", totalVolume: { $sum: "$amount" }, count: { $sum: 1 } } },
  { $sort: { totalVolume: -1 } }
]);</code></pre>
  </div>
  <div class="qa-block">
    <span class="q-title">Mongoose Optimization (lean):</span> <code>User.find().lean()</code> skips converting documents into heavy Mongoose hydrated instances, returning plain JS objects for significantly faster reads.
  </div>
  <h1>5. React Native Fundamentals</h1>
  <ul>
    <li><strong>Core Architecture:</strong> Runs JavaScript logic on a background thread communicating with native Android/iOS UI primitives via the bridge/JSI.</li>
    <li><strong>Element Mapping:</strong> <code>&lt;div&gt;</code> $\rightarrow$ <code>&lt;View&gt;</code> | <code>&lt;p&gt;/&lt;span&gt;</code> $\rightarrow$ <code>&lt;Text&gt;</code> | <code>&lt;button&gt;</code> $\rightarrow$ <code>&lt;TouchableOpacity&gt;</code> / <code>&lt;Pressable&gt;</code>.</li>
    <li><strong>List Performance:</strong> <code>&lt;FlatList&gt;</code> renders only visible onscreen items to optimize performance during scrolling through transaction records.</li>
    <li><strong>Flexbox Defaults:</strong> React Native defaults to <code>flexDirection: 'column'</code> instead of web's <code>row</code>.</li>
  </ul>
  <h1>6. Real-Time FinTech Interview Scenarios</h1>
  <div class="qa-block">
    <span class="q-title">Preventing Double-Spending / Concurrency Collisions:</span>
    Use MongoDB atomic updates with balance check conditions or ACID multi-document transactions:
<pre><code>const result = await Wallet.updateOne(
  { userId: senderId, balance: { $gte: debitAmount } },
  { $inc: { balance: -debitAmount } }
);
if (result.matchedCount === 0) throw new Error("Insufficient balance or concurrency lock");</code></pre>
  </div>



