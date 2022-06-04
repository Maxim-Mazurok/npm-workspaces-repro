# npm workspaces issue when using different versions of the same package

## Reproduction

1. Git clone
2. Use node `v18.3.0` and `npm@8.12.1`: `nvm i 18.3.0` or `nvs add 18.3.0 && nvs use 18.3.0`
3. `npm ci`
4. `npm test`

Expected:

```text
"testing jest-26"
26.6.3 <<< expected

"testing jest-28"
28.1.0
```

Actual:

```text
"testing jest-26"
28.1.0 <<< unexpected

"testing jest-28"
28.1.0
```

## Workaround

Use jest programmatically: `node -e "console.log(require('jest').getVersion())"`

See `npm run workaround`
