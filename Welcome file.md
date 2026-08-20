---


---




  
  <title>MERN &amp; React Native Technical Interview Guide</title>
  


  <div class="header-box">
    <h2>Full-Stack Technical Interview Master Guide</h2>
    <p><strong>Target Stack:</strong> JavaScript (ES6+), React.js, Node.js, Express, MongoDB, React Native</p>
    <p><strong>Focus Domain:</strong> FinTech / Real-time Digital Payment Architectures</p>
  </div>
  <h1>1. JavaScript Fundamentals &amp; ES6+</h1>
  <h3>Core Concepts &amp; Scope</h3>
  <ul>
    <li><strong><code>var</code> vs <code>let</code> vs <code>const</code>:</strong> <code>var</code> is function-scoped and hoisted with <code>undefined</code>. <code>let</code> and <code>const</code> are block-scoped and hoisted into a Temporal Dead Zone (TDZ). <code>const</code> variables cannot be reassigned.</li>
    <li><strong>Data Types:</strong> Primitive (<code>string</code>, <code>number</code>, <code>bigint</code>, <code>boolean</code>, <code>undefined</code>, <code>symbol</code>, <code>null</code>) and Non-Primitive (<code>Object</code>, <code>Array</code>, <code>Function</code>).</li>
    <li><strong><code>==</code> vs <code>===</code>:</strong> <code>==</code> compares values with type coercion (<code>5 == "5"</code> is true). <code>===</code> performs strict equality checks without coercion.</li>
    <li><strong>Hoisting:</strong> JavaScript's engine moves declarations to top of their scope before execution. Functions are hoisted with their body; <code>var</code> initialized to <code>undefined</code>; <code>let</code>/<code>const</code> uninitialized (TDZ).</li>
    <li><strong>Closures:</strong> A function bundled with references to its outer lexical environment, preserving variables even after the outer function executes.</li>
    <li><strong>Shallow vs Deep Copy:</strong> Shallow copy (<code>Object.assign</code>, <code>{...obj}</code>) duplicates top-level references. Deep copy (<code>structuredClone(obj)</code>) recursively duplicates all nested objects.</li>
  </ul>
  <h3>Functions, Objects &amp; Async JS</h3>
  <ul>
    <li><strong>Arrow Functions:</strong> Shorter syntax without their own <code>this</code>, <code>arguments</code>, or <code>prototype</code> (inherits <code>this</code> lexically).</li>
    <li><strong><code>call()</code>, <code>apply()</code>, <code>bind()</code>:</strong> <code>call</code> passes comma arguments immediately, <code>apply</code> passes array arguments immediately, <code>bind</code> returns a bound function for later execution.</li>
    <li><strong>Event Loop:</strong> Executes synchronous code on the Call Stack, drains Microtask queue (Promises), then picks tasks from the Macrotask queue (<code>setTimeout</code>, I/O).</li>
  </ul>
<pre><code>// Async/Await API Request Example
async function getWalletData(userId) {
  try {
    const res = await fetch(`/api/wallet/${userId}`);
    return await res.json();
  } catch (err) {
    console.error("Fetch failed:", err);
  }
}</code></pre>
  <h1>2. React.js</h1>
  <ul>
    <li><strong>Virtual DOM:</strong> In-memory lightweight representation of the real DOM. Updates trigger a diffing algorithm (Reconciliation) to compute minimal UI mutations.</li>
    <li><strong>Props vs State:</strong> Props are immutable parameters passed down from parents; State represents local, mutable component data.</li>
    <li><strong>Core Hooks:</strong>
      <ul>
        <li><code>useState</code>: Declares reactive state.</li>
        <li><code>useEffect</code>: Handles side-effects (data fetching, DOM subscriptions).</li>
        <li><code>useRef</code>: Persists mutable references across renders without re-rendering.</li>
        <li><code>useContext</code>: Consumes Context values without nested consumers.</li>
        <li><code>useMemo</code>: Caches computed values across renders.</li>
        <li><code>useCallback</code>: Caches function instances to avoid re-renders of memoized child components.</li>
      </ul>
    </li>
    <li><strong><code>React.memo</code>:</strong> Higher-order component preventing unnecessary re-renders when incoming props remain unchanged.</li>
  </ul>
  <h1>3. Node.js &amp; Express.js</h1>
  <ul>
    <li><strong>Runtime Architecture:</strong> Single-threaded event loop powered by Google V8 and <strong>libuv</strong> (which handles async I/O and thread pooling for file/crypto operations).</li>
    <li><strong>Streams vs Buffers:</strong> <code>fs.createReadStream()</code> streams data in manageable chunks, preventing memory overflow caused by <code>fs.readFile()</code> on large payloads.</li>
    <li><strong>Express Middleware:</strong> Functions receiving <code>(req, res, next)</code> to parse requests, validate auth tokens, and handle exceptions.</li>
  </ul>
<pre><code>// Authentication Middleware
const authMiddleware = (req, res, next) =&gt; {
  const token = req.headers.authorization;
  if (!token) return res.status(401).json({ message: "Unauthorized" });
  // Verify token logic
  next();
};</code></pre>
  <h1>4. MongoDB &amp; Mongoose</h1>
  <table>
    <thead>
      <tr>
        <th>Feature</th>
        <th>Relational (SQL)</th>
        <th>MongoDB (NoSQL)</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><strong>Format</strong></td>
        <td>Structured Tables / Rows</td>
        <td>BSON (Binary JSON) Documents</td>
      </tr>
      <tr>
        <td><strong>Schema</strong></td>
        <td>Rigid / Migrations required</td>
        <td>Flexible / Dynamic</td>
      </tr>
      <tr>
        <td><strong>Relations</strong></td>
        <td>Foreign Keys &amp; JOINs</td>
        <td>Embedded Documents or $lookup</td>
      </tr>
      <tr>
        <td><strong>Scaling</strong></td>
        <td>Vertical</td>
        <td>Horizontal (Sharding)</td>
      </tr>
    </tbody>
  </table>
  <ul>
    <li><strong>Indexing:</strong> Creates B-tree structures over document keys to eliminate full collection scans and speed up query lookups.</li>
    <li><strong>Aggregation Pipeline:</strong> Multi-stage processing arrays (e.g., <code>$match</code>, <code>$group</code>, <code>$sort</code>, <code>$project</code>).</li>
    <li><strong><code>.lean()</code>:</strong> Skips Mongoose document hydration, returning plain JS objects for much faster read performance.</li>
  </ul>
  <h1>5. React Native Fundamentals</h1>
  <ul>
    <li><strong>Architecture:</strong> Directly invokes native iOS/Android interface widgets via a JavaScript bridge/JSI.</li>
    <li><strong>Primitives:</strong> <code>&lt;View&gt;</code> (div), <code>&lt;Text&gt;</code> (p/span), <code>&lt;TouchableOpacity&gt;</code> / <code>&lt;Pressable&gt;</code> (button), <code>&lt;FlatList&gt;</code> (efficient virtualized lists).</li>
    <li><strong>Layout:</strong> Uses Flexbox by default with <code>flexDirection: 'column'</code>.</li>
  </ul>
  <h1>6. FinTech Practical Scenarios</h1>
  <ul>
    <li><strong>Race Conditions &amp; Double-Spending:</strong> Prevented using MongoDB atomic updates (<code>$inc</code> with conditional checks like <code>{ balance: { $gte: amount } }</code>) or multi-document ACID transactions via <code>session.startTransaction()</code>.</li>
    <li><strong>Secure Auth:</strong> JWT authentication using <code>HttpOnly</code>, <code>Secure</code> cookies for refresh tokens and short-lived access tokens via authorization headers.</li>
  </ul>




  
  <title>MERN &amp; React Native Technical Interview Guide</title>
  


  <div class="header-box">
    <h2>Full-Stack Technical Interview Master Guide</h2>
    <p><strong>Target Stack:</strong> JavaScript (ES6+), React.js, Node.js, Express, MongoDB, React Native</p>
    <p><strong>Focus Domain:</strong> FinTech / Real-time Digital Payment Architectures</p>
  </div>
  <h1>1. JavaScript Fundamentals &amp; ES6+</h1>
  <h3>Core Concepts &amp; Scope</h3>
  <ul>
    <li><strong><code>var</code> vs <code>let</code> vs <code>const</code>:</strong> <code>var</code> is function-scoped and hoisted with <code>undefined</code>. <code>let</code> and <code>const</code> are block-scoped and hoisted into a Temporal Dead Zone (TDZ). <code>const</code> variables cannot be reassigned.</li>
    <li><strong>Data Types:</strong> Primitive (<code>string</code>, <code>number</code>, <code>bigint</code>, <code>boolean</code>, <code>undefined</code>, <code>symbol</code>, <code>null</code>) and Non-Primitive (<code>Object</code>, <code>Array</code>, <code>Function</code>).</li>
    <li><strong><code>==</code> vs <code>===</code>:</strong> <code>==</code> compares values with type coercion (<code>5 == "5"</code> is true). <code>===</code> performs strict equality checks without coercion.</li>
    <li><strong>Hoisting:</strong> JavaScript's engine moves declarations to top of their scope before execution. Functions are hoisted with their body; <code>var</code> initialized to <code>undefined</code>; <code>let</code>/<code>const</code> uninitialized (TDZ).</li>
    <li><strong>Closures:</strong> A function bundled with references to its outer lexical environment, preserving variables even after the outer function executes.</li>
    <li><strong>Shallow vs Deep Copy:</strong> Shallow copy (<code>Object.assign</code>, <code>{...obj}</code>) duplicates top-level references. Deep copy (<code>structuredClone(obj)</code>) recursively duplicates all nested objects.</li>
  </ul>
  <h3>Functions, Objects &amp; Async JS</h3>
  <ul>
    <li><strong>Arrow Functions:</strong> Shorter syntax without their own <code>this</code>, <code>arguments</code>, or <code>prototype</code> (inherits <code>this</code> lexically).</li>
    <li><strong><code>call()</code>, <code>apply()</code>, <code>bind()</code>:</strong> <code>call</code> passes comma arguments immediately, <code>apply</code> passes array arguments immediately, <code>bind</code> returns a bound function for later execution.</li>
    <li><strong>Event Loop:</strong> Executes synchronous code on the Call Stack, drains Microtask queue (Promises), then picks tasks from the Macrotask queue (<code>setTimeout</code>, I/O).</li>
  </ul>
<pre><code>// Async/Await API Request Example
async function getWalletData(userId) {
  try {
    const res = await fetch(`/api/wallet/${userId}`);
    return await res.json();
  } catch (err) {
    console.error("Fetch failed:", err);
  }
}</code></pre>
  <h1>2. React.js</h1>
  <ul>
    <li><strong>Virtual DOM:</strong> In-memory lightweight representation of the real DOM. Updates trigger a diffing algorithm (Reconciliation) to compute minimal UI mutations.</li>
    <li><strong>Props vs State:</strong> Props are immutable parameters passed down from parents; State represents local, mutable component data.</li>
    <li><strong>Core Hooks:</strong>
      <ul>
        <li><code>useState</code>: Declares reactive state.</li>
        <li><code>useEffect</code>: Handles side-effects (data fetching, DOM subscriptions).</li>
        <li><code>useRef</code>: Persists mutable references across renders without re-rendering.</li>
        <li><code>useContext</code>: Consumes Context values without nested consumers.</li>
        <li><code>useMemo</code>: Caches computed values across renders.</li>
        <li><code>useCallback</code>: Caches function instances to avoid re-renders of memoized child components.</li>
      </ul>
    </li>
    <li><strong><code>React.memo</code>:</strong> Higher-order component preventing unnecessary re-renders when incoming props remain unchanged.</li>
  </ul>
  <h1>3. Node.js &amp; Express.js</h1>
  <ul>
    <li><strong>Runtime Architecture:</strong> Single-threaded event loop powered by Google V8 and <strong>libuv</strong> (which handles async I/O and thread pooling for file/crypto operations).</li>
    <li><strong>Streams vs Buffers:</strong> <code>fs.createReadStream()</code> streams data in manageable chunks, preventing memory overflow caused by <code>fs.readFile()</code> on large payloads.</li>
    <li><strong>Express Middleware:</strong> Functions receiving <code>(req, res, next)</code> to parse requests, validate auth tokens, and handle exceptions.</li>
  </ul>
<pre><code>// Authentication Middleware
const authMiddleware = (req, res, next) =&gt; {
  const token = req.headers.authorization;
  if (!token) return res.status(401).json({ message: "Unauthorized" });
  // Verify token logic
  next();
};</code></pre>
  <h1>4. MongoDB &amp; Mongoose</h1>
  <table>
    <thead>
      <tr>
        <th>Feature</th>
        <th>Relational (SQL)</th>
        <th>MongoDB (NoSQL)</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><strong>Format</strong></td>
        <td>Structured Tables / Rows</td>
        <td>BSON (Binary JSON) Documents</td>
      </tr>
      <tr>
        <td><strong>Schema</strong></td>
        <td>Rigid / Migrations required</td>
        <td>Flexible / Dynamic</td>
      </tr>
      <tr>
        <td><strong>Relations</strong></td>
        <td>Foreign Keys &amp; JOINs</td>
        <td>Embedded Documents or $lookup</td>
      </tr>
      <tr>
        <td><strong>Scaling</strong></td>
        <td>Vertical</td>
        <td>Horizontal (Sharding)</td>
      </tr>
    </tbody>
  </table>
  <ul>
    <li><strong>Indexing:</strong> Creates B-tree structures over document keys to eliminate full collection scans and speed up query lookups.</li>
    <li><strong>Aggregation Pipeline:</strong> Multi-stage processing arrays (e.g., <code>$match</code>, <code>$group</code>, <code>$sort</code>, <code>$project</code>).</li>
    <li><strong><code>.lean()</code>:</strong> Skips Mongoose document hydration, returning plain JS objects for much faster read performance.</li>
  </ul>
  <h1>5. React Native Fundamentals</h1>
  <ul>
    <li><strong>Architecture:</strong> Directly invokes native iOS/Android interface widgets via a JavaScript bridge/JSI.</li>
    <li><strong>Primitives:</strong> <code>&lt;View&gt;</code> (div), <code>&lt;Text&gt;</code> (p/span), <code>&lt;TouchableOpacity&gt;</code> / <code>&lt;Pressable&gt;</code> (button), <code>&lt;FlatList&gt;</code> (efficient virtualized lists).</li>
    <li><strong>Layout:</strong> Uses Flexbox by default with <code>flexDirection: 'column'</code>.</li>
  </ul>
  <h1>6. FinTech Practical Scenarios</h1>
  <ul>
    <li><strong>Race Conditions &amp; Double-Spending:</strong> Prevented using MongoDB atomic updates (<code>$inc</code> with conditional checks like <code>{ balance: { $gte: amount } }</code>) or multi-document ACID transactions via <code>session.startTransaction()</code>.</li>
    <li><strong>Secure Auth:</strong> JWT authentication using <code>HttpOnly</code>, <code>Secure</code> cookies for refresh tokens and short-lived access tokens via authorization headers.</li>
  </ul>



