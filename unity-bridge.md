# Optional Unity host page bridge

Add this to your separately hosted Unity WebGL HTML page around the existing loader promise. Replace the allowed portfolio origin with the exact deployed HTTPS origin. Do not use `*`. Keep your actual loader URL, canvas reference, and Unity configuration unchanged.

```js
const portfolioOrigin = 'https://nom-ali.github.io';
// This wraps your existing call; do not instantiate the build a second time.
createUnityInstance(canvas, config, (progress) => {
  // Keep the game's own Unity loading progress UI here.
}).then((unityInstance) => {
  window.parent.postMessage({ type: 'unity-ready' }, portfolioOrigin);
}).catch((error) => {
  console.error('Unity initialization failed', error);
  window.parent.postMessage({ type: 'unity-error' }, portfolioOrigin);
  // Keep the game's standalone error UI here too.
});
```

The portfolio accepts these messages only from the active iframe and its exact origin. It does not execute message content. A remote site blocking iframes cannot be repaired by this bridge; use the external-open link instead.
