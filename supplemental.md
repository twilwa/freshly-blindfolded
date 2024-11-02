Project Path: elizas-xyz

Source Tree:

```
elizas-xyz
├── package.json
├── LICENSE
├── postcss.config.js
├── tailwind.config.js
├── src
│   ├── index.css
│   ├── pages
│   │   └── Landing.tsx
│   ├── components
│   │   ├── Navbar.tsx
│   │   ├── ConnectWallet.tsx
│   │   └── EmailSignup.tsx
│   ├── lib
│   │   ├── particle.tsx
│   │   ├── supabase.ts
│   │   └── particle.ts
│   ├── App.tsx
│   └── main.tsx
├── README.md
├── index.html
└── package-lock.json

```

`/home/anon/repos/elizas-xyz/package.json`:

```json
{
  "name": "elizas-marketplace",
  "private": true,
  "version": "0.1.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "lint": "eslint . --ext ts,tsx --report-unused-disable-directives --max-warnings 0",
    "preview": "vite preview"
  },
  "dependencies": {
    "@particle-network/connectkit": "^1.0.0",
    "@supabase/supabase-js": "^2.39.0",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.20.1",
    "viem": "^2.0.0",
    "zustand": "^4.4.7"
  },
  "devDependencies": {
    "@types/react": "^18.2.37",
    "@types/react-dom": "^18.2.15",
    "@typescript-eslint/eslint-plugin": "^6.10.0",
    "@typescript-eslint/parser": "^6.10.0",
    "@vitejs/plugin-react": "^4.2.0",
    "autoprefixer": "^10.4.16",
    "daisyui": "^4.4.19",
    "eslint": "^8.53.0",
    "eslint-plugin-react-hooks": "^4.6.0",
    "eslint-plugin-react-refresh": "^0.4.4",
    "postcss": "^8.4.32",
    "tailwindcss": "^3.3.6",
    "typescript": "^5.2.2",
    "vite": "^5.0.0"
  }
}
```

`/home/anon/repos/elizas-xyz/LICENSE`:

```
MIT License

Copyright (c) 2024 elizas.xyz

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

```

`/home/anon/repos/elizas-xyz/postcss.config.js`:

```js
export default {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
```

`/home/anon/repos/elizas-xyz/tailwind.config.js`:

```js
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {
      colors: {
        'ai16z': {
          orange: '#FF6B00',
          dark: '#1C1C1C',
          gray: '#2D2D2D',
        },
      },
    },
  },
  plugins: [require("daisyui")],
  daisyui: {
    themes: ["light", "dark"],
  },
}
```

`/home/anon/repos/elizas-xyz/src/index.css`:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;

body {
  background-color: #1C1C1C;
  color: #ffffff;
}

.particle-connect-button {
  background-color: #FF6B00 !important;
  color: white !important;
  border: none !important;
}

.particle-connect-button:hover {
  background-color: #E65000 !important;
}
```

`/home/anon/repos/elizas-xyz/src/pages/Landing.tsx`:

```tsx
import React from 'react';
import { EmailSignup } from '../components/EmailSignup';

export const Landing: React.FC = () => {
  const handleEmailSubmit = async (email: string) => {
    try {
      console.log('Email submitted:', email);
      // TODO: Implement Supabase integration
    } catch (error) {
      console.error('Error submitting email:', error);
    }
  };

  return (
    <div className="container mx-auto px-4 py-16">
      <div className="flex flex-col items-center justify-center">
        <h1 className="text-5xl md:text-6xl font-bold mb-8 text-white text-center">
          Welcome to <span className="text-ai16z-orange">Elizas</span>
        </h1>
        <p className="text-xl md:text-2xl mb-12 text-gray-300 text-center max-w-3xl">
          The premier marketplace for AI agents. Create, discover, and utilize
          powerful AI assistants for your needs.
        </p>
        <div className="flex flex-col md:flex-row justify-center items-stretch gap-8 w-full max-w-5xl">
          <EmailSignup type="creator" onSubmit={handleEmailSubmit} />
          <EmailSignup type="client" onSubmit={handleEmailSubmit} />
        </div>
      </div>
    </div>
  );
};
```

`/home/anon/repos/elizas-xyz/src/components/Navbar.tsx`:

```tsx
import React from 'react';
import { Link } from 'react-router-dom';
import { ConnectWallet } from './ConnectWallet';

export const Navbar: React.FC = () => {
  return (
    <div className="navbar bg-[#1C1C1C] border-b border-[#2D2D2D]">
      <div className="container mx-auto px-4">
        <div className="flex-1">
          <Link to="/" className="text-[#FF6B00] text-2xl font-bold">
            Elizas.xyz
          </Link>
        </div>
        <div className="flex-none">
          <ul className="menu menu-horizontal px-1">
            <li>
              <Link to="/marketplace" className="text-white hover:text-[#FF6B00]">
                Marketplace
              </Link>
            </li>
            <li>
              <Link to="/dashboard" className="text-white hover:text-[#FF6B00]">
                Dashboard
              </Link>
            </li>
          </ul>
          <div className="ml-4">
            <ConnectWallet />
          </div>
        </div>
      </div>
    </div>
  );
};
```

`/home/anon/repos/elizas-xyz/src/components/ConnectWallet.tsx`:

```tsx
import React from 'react';
import { ConnectButton } from '@particle-network/connectkit';
import '@particle-network/connectkit/dist/index.css';

export const ConnectWallet: React.FC = () => {
  return (
    <ConnectButton.Custom>
      {({ account, isConnecting, show }) => (
        <button
          onClick={show}
          disabled={isConnecting}
          className="btn bg-ai16z-orange hover:bg-[#E65000] text-white border-none"
        >
          {isConnecting ? 'Connecting...' : account ? `${account.slice(0, 6)}...${account.slice(-4)}` : 'Connect Wallet'}
        </button>
      )}
    </ConnectButton.Custom>
  );
};
```

`/home/anon/repos/elizas-xyz/src/components/EmailSignup.tsx`:

```tsx
import React, { useState } from 'react';

interface EmailSignupProps {
  type: 'creator' | 'client';
  onSubmit: (email: string) => void;
}

export const EmailSignup: React.FC<EmailSignupProps> = ({ type, onSubmit }) => {
  const [email, setEmail] = useState('');
  const [isSubmitting, setIsSubmitting] = useState(false);

  const handleSubmit = async (e: React.FormEvent) => {
    e.preventDefault();
    setIsSubmitting(true);
    try {
      await onSubmit(email);
      setEmail('');
    } finally {
      setIsSubmitting(false);
    }
  };

  return (
    <div className="card w-full md:w-96 bg-ai16z-gray border border-gray-700">
      <div className="card-body">
        <h2 className="card-title text-white">
          {type === 'creator' ? 'Create Elizas' : 'Find Elizas'}
        </h2>
        <p className="text-gray-300">
          {type === 'creator'
            ? 'Join as a creator and build amazing AI agents'
            : 'Discover AI agents that can help with your tasks'}
        </p>
        <form onSubmit={handleSubmit} className="form-control mt-4">
          <input
            type="email"
            placeholder="Enter your email"
            className="input bg-ai16z-dark border-gray-700 text-white placeholder-gray-400 w-full"
            value={email}
            onChange={(e) => setEmail(e.target.value)}
            disabled={isSubmitting}
            required
          />
          <button 
            className={`btn bg-ai16z-orange hover:bg-orange-700 border-none text-white mt-4 w-full ${isSubmitting ? 'loading' : ''}`}
            disabled={isSubmitting}
          >
            Join Waitlist
          </button>
        </form>
      </div>
    </div>
  );
};
```

`/home/anon/repos/elizas-xyz/src/lib/particle.tsx`:

```tsx
import React from 'react';
import { ConnectKitProvider, createConfig } from '@particle-network/connectkit';
import { Ethereum } from '@particle-network/connectkit/chains';
import { evmWalletConnectors } from '@particle-network/connectkit/evm';
import { authWalletConnectors } from '@particle-network/connectkit/auth';
import { wallet, EntryPosition } from '@particle-network/connectkit/wallet';

const config = createConfig({
  projectId: import.meta.env.VITE_PARTICLE_PROJECT_ID as string,
  clientKey: import.meta.env.VITE_PARTICLE_CLIENT_KEY as string,
  appId: import.meta.env.VITE_PARTICLE_APP_ID as string,
  chains: [Ethereum],
  walletConnectors: [
    evmWalletConnectors({
      metadata: {
        name: 'Elizas.xyz',
        description: 'AI Agent Marketplace',
        url: 'https://elizas.xyz',
        icons: ['https://elizas.xyz/logo.png']
      }
    }),
    authWalletConnectors({
      authTypes: ['email', 'google', 'twitter', 'github'],
      fiatCoin: 'USD',
      promptSettingConfig: {
        promptMasterPasswordSettingWhenLogin: 1,
        promptPaymentPasswordSettingWhenSign: 1,
      },
    }),
  ],
  appearance: {
    theme: {
      '--pcm-accent-color': '#FF6B00',
      '--pcm-primary-button-background': '#FF6B00',
      '--pcm-primary-button-hover-background': '#E65000',
    },
  },
  plugins: [
    wallet({
      visible: true,
      entryPosition: EntryPosition.BR,
    }),
  ],
});

export const ParticleProvider: React.FC<{ children: React.ReactNode }> = ({ children }) => {
  return (
    <ConnectKitProvider config={config}>
      {children}
    </ConnectKitProvider>
  );
};
```

`/home/anon/repos/elizas-xyz/src/lib/supabase.ts`:

```ts
import { createClient } from '@supabase/supabase-js';

const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseAnonKey = import.meta.env.VITE_SUPABASE_ANON_KEY;

export const supabase = createClient(supabaseUrl, supabaseAnonKey);
```

`/home/anon/repos/elizas-xyz/src/lib/particle.ts`:

```ts
import { ParticleNetwork } from '@particle-network/auth';
import { WalletEntryPosition } from '@particle-network/connect';
import { Ethereum } from '@particle-network/chains';

export const particle = new ParticleNetwork({
  projectId: import.meta.env.VITE_PARTICLE_PROJECT_ID,
  clientKey: import.meta.env.VITE_PARTICLE_CLIENT_KEY,
  appId: import.meta.env.VITE_PARTICLE_APP_ID,
  chainName: Ethereum.name,
  chainId: Ethereum.id,
  wallet: {
    displayWalletEntry: true,
    defaultWalletEntryPosition: WalletEntryPosition.BR,
    supportChains: [Ethereum],
  },
});
```

`/home/anon/repos/elizas-xyz/src/App.tsx`:

```tsx
import React from 'react';
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
import { ConnectProvider } from '@particle-network/connect-react-ui';
import { Ethereum } from '@particle-network/chains';
import { Navbar } from './components/Navbar';
import { Landing } from './pages/Landing';

function App() {
  return (
    <ConnectProvider
      options={{
        projectId: import.meta.env.VITE_PARTICLE_PROJECT_ID as string,
        clientKey: import.meta.env.VITE_PARTICLE_CLIENT_KEY as string,
        appId: import.meta.env.VITE_PARTICLE_APP_ID as string,
        chains: [Ethereum],
      }}
    >
      <Router>
        <div className="min-h-screen bg-[#1C1C1C] flex flex-col">
          <Navbar />
          <main className="flex-grow">
            <Routes>
              <Route path="/" element={<Landing />} />
            </Routes>
          </main>
        </div>
      </Router>
    </ConnectProvider>
  );
}

export default App;
```

`/home/anon/repos/elizas-xyz/src/main.tsx`:

```tsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';
import './index.css';
import { ParticleProvider } from './lib/particle';

ReactDOM.createRoot(document.getElementById('root')!).render(
  <React.StrictMode>
    <ParticleProvider>
      <App />
    </ParticleProvider>
  </React.StrictMode>,
);
```

`/home/anon/repos/elizas-xyz/README.md`:

```md
# elizas-xyz
landing page

```

`/home/anon/repos/elizas-xyz/index.html`:

```html
<!DOCTYPE html>
<html lang="en" data-theme="ai16z">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Elizas.xyz - AI Agent Marketplace</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>
```

`/home/anon/repos/elizas-xyz/package-lock.json`:

```json
{
  "name": "elizas-marketplace",
  "version": "0.1.0",
  "lockfileVersion": 3,
  "requires": true,
  "packages": {
    "": {
      "name": "elizas-marketplace",
      "version": "0.1.0",
      "dependencies": {
        "@particle-network/connectkit": "^1.0.0",
        "@supabase/supabase-js": "^2.39.0",
        "react": "^18.2.0",
        "react-dom": "^18.2.0",
        "react-router-dom": "^6.20.1",
        "viem": "^2.0.0",
        "zustand": "^4.4.7"
      },
      "devDependencies": {
        "@types/react": "^18.2.37",
        "@types/react-dom": "^18.2.15",
        "@typescript-eslint/eslint-plugin": "^6.10.0",
        "@typescript-eslint/parser": "^6.10.0",
        "@vitejs/plugin-react": "^4.2.0",
        "autoprefixer": "^10.4.16",
        "daisyui": "^4.4.19",
        "eslint": "^8.53.0",
        "eslint-plugin-react-hooks": "^4.6.0",
        "eslint-plugin-react-refresh": "^0.4.4",
        "postcss": "^8.4.32",
        "tailwindcss": "^3.3.6",
        "typescript": "^5.2.2",
        "vite": "^5.0.0"
      }
    },
    "node_modules/@adraffy/ens-normalize": {
      "version": "1.11.0",
      "resolved": "https://registry.npmjs.org/@adraffy/ens-normalize/-/ens-normalize-1.11.0.tgz",
      "integrity": "sha512-/3DDPKHqqIqxUULp8yP4zODUY1i+2xvVWsv8A79xGWdCAG+8sb0hRh0Rk2QyOJUnnbyPUAZYcpBuRe3nS2OIUg=="
    },
    "node_modules/@alloc/quick-lru": {
      "version": "5.2.0",
      "resolved": "https://registry.npmjs.org/@alloc/quick-lru/-/quick-lru-5.2.0.tgz",
      "integrity": "sha512-UrcABB+4bUrFABwbluTIBErXwvbsU/V7TZWfmbgJfbkwiBuziS9gxdODUyuiecfdGQ85jglMW6juS3+z5TsKLw==",
      "dev": true,
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/@ampproject/remapping": {
      "version": "2.3.0",
      "resolved": "https://registry.npmjs.org/@ampproject/remapping/-/remapping-2.3.0.tgz",
      "integrity": "sha512-30iZtAPgz+LTIYoeivqYo853f02jBYSd5uGnGpkFV0M3xOt9aN73erkgYAmZU43x4VfqcnLxW9Kpg3R5LC4YYw==",
      "dev": true,
      "dependencies": {
        "@jridgewell/gen-mapping": "^0.3.5",
        "@jridgewell/trace-mapping": "^0.3.24"
      },
      "engines": {
        "node": ">=6.0.0"
      }
    },
    "node_modules/@ant-design/colors": {
      "version": "6.0.0",
      "resolved": "https://registry.npmjs.org/@ant-design/colors/-/colors-6.0.0.tgz",
      "integrity": "sha512-qAZRvPzfdWHtfameEGP2Qvuf838NhergR35o+EuVyB5XvSA98xod5r4utvi4TJ3ywmevm290g9nsCG5MryrdWQ==",
      "dependencies": {
        "@ctrl/tinycolor": "^3.4.0"
      }
    },
    "node_modules/@ant-design/icons": {
      "version": "4.8.3",
      "resolved": "https://registry.npmjs.org/@ant-design/icons/-/icons-4.8.3.tgz",
      "integrity": "sha512-HGlIQZzrEbAhpJR6+IGdzfbPym94Owr6JZkJ2QCCnOkPVIWMO2xgIVcOKnl8YcpijIo39V7l2qQL5fmtw56cMw==",
      "dependencies": {
        "@ant-design/colors": "^6.0.0",
        "@ant-design/icons-svg": "^4.3.0",
        "@babel/runtime": "^7.11.2",
        "classnames": "^2.2.6",
        "lodash": "^4.17.15",
        "rc-util": "^5.9.4"
      },
      "engines": {
        "node": ">=8"
      },
      "peerDependencies": {
        "react": ">=16.0.0",
        "react-dom": ">=16.0.0"
      }
    },
    "node_modules/@ant-design/icons-svg": {
      "version": "4.4.2",
      "resolved": "https://registry.npmjs.org/@ant-design/icons-svg/-/icons-svg-4.4.2.tgz",
      "integrity": "sha512-vHbT+zJEVzllwP+CM+ul7reTEfBR0vgxFe7+lREAsAA7YGsYpboiq2sQNeQeRvh09GfQgs/GyFEvZpJ9cLXpXA=="
    },
    "node_modules/@ant-design/react-slick": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/@ant-design/react-slick/-/react-slick-1.0.2.tgz",
      "integrity": "sha512-Wj8onxL/T8KQLFFiCA4t8eIRGpRR+UPgOdac2sYzonv+i0n3kXHmvHLLiOYL655DQx2Umii9Y9nNgL7ssu5haQ==",
      "dependencies": {
        "@babel/runtime": "^7.10.4",
        "classnames": "^2.2.5",
        "json2mq": "^0.2.0",
        "resize-observer-polyfill": "^1.5.1",
        "throttle-debounce": "^5.0.0"
      },
      "peerDependencies": {
        "react": ">=16.9.0"
      }
    },
    "node_modules/@aws-crypto/sha256-browser": {
      "version": "5.2.0",
      "resolved": "https://registry.npmjs.org/@aws-crypto/sha256-browser/-/sha256-browser-5.2.0.tgz",
      "integrity": "sha512-AXfN/lGotSQwu6HNcEsIASo7kWXZ5HYWvfOmSNKDsEqC4OashTp8alTmaz+F7TC2L083SFv5RdB+qU3Vs1kZqw==",
      "dependencies": {
        "@aws-crypto/sha256-js": "^5.2.0",
        "@aws-crypto/supports-web-crypto": "^5.2.0",
        "@aws-crypto/util": "^5.2.0",
        "@aws-sdk/types": "^3.222.0",
        "@aws-sdk/util-locate-window": "^3.0.0",
        "@smithy/util-utf8": "^2.0.0",
        "tslib": "^2.6.2"
      }
    },
    "node_modules/@aws-crypto/sha256-browser/node_modules/@smithy/is-array-buffer": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/@smithy/is-array-buffer/-/is-array-buffer-2.2.0.tgz",
      "integrity": "sha512-GGP3O9QFD24uGeAXYUjwSTXARoqpZykHadOmA8G5vfJPK0/DC67qa//0qvqrJzL1xc8WQWX7/yc7fwudjPHPhA==",
      "dependencies": {
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=14.0.0"
      }
    },
    "node_modules/@aws-crypto/sha256-browser/node_modules/@smithy/util-buffer-from": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/@smithy/util-buffer-from/-/util-buffer-from-2.2.0.tgz",
      "integrity": "sha512-IJdWBbTcMQ6DA0gdNhh/BwrLkDR+ADW5Kr1aZmd4k3DIF6ezMV4R2NIAmT08wQJ3yUK82thHWmC/TnK/wpMMIA==",
      "dependencies": {
        "@smithy/is-array-buffer": "^2.2.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=14.0.0"
      }
    },
    "node_modules/@aws-crypto/sha256-browser/node_modules/@smithy/util-utf8": {
      "version": "2.3.0",
      "resolved": "https://registry.npmjs.org/@smithy/util-utf8/-/util-utf8-2.3.0.tgz",
      "integrity": "sha512-R8Rdn8Hy72KKcebgLiv8jQcQkXoLMOGGv5uI1/k0l+snqkOzQ1R0ChUBCxWMlBsFMekWjq0wRudIweFs7sKT5A==",
      "dependencies": {
        "@smithy/util-buffer-from": "^2.2.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=14.0.0"
      }
    },
    "node_modules/@aws-crypto/sha256-browser/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-crypto/sha256-js": {
      "version": "5.2.0",
      "resolved": "https://registry.npmjs.org/@aws-crypto/sha256-js/-/sha256-js-5.2.0.tgz",
      "integrity": "sha512-FFQQyu7edu4ufvIZ+OadFpHHOt+eSTBaYaki44c+akjg7qZg9oOQeLlk77F6tSYqjDAFClrHJk9tMf0HdVyOvA==",
      "dependencies": {
        "@aws-crypto/util": "^5.2.0",
        "@aws-sdk/types": "^3.222.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-crypto/sha256-js/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-crypto/supports-web-crypto": {
      "version": "5.2.0",
      "resolved": "https://registry.npmjs.org/@aws-crypto/supports-web-crypto/-/supports-web-crypto-5.2.0.tgz",
      "integrity": "sha512-iAvUotm021kM33eCdNfwIN//F77/IADDSs58i+MDaOqFrVjZo9bAal0NK7HurRuWLLpF1iLX7gbWrjHjeo+YFg==",
      "dependencies": {
        "tslib": "^2.6.2"
      }
    },
    "node_modules/@aws-crypto/supports-web-crypto/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-crypto/util": {
      "version": "5.2.0",
      "resolved": "https://registry.npmjs.org/@aws-crypto/util/-/util-5.2.0.tgz",
      "integrity": "sha512-4RkU9EsI6ZpBve5fseQlGNUWKMa1RLPQ1dnjnQoe07ldfIzcsGb5hC5W0Dm7u423KWzawlrpbjXBrXCEv9zazQ==",
      "dependencies": {
        "@aws-sdk/types": "^3.222.0",
        "@smithy/util-utf8": "^2.0.0",
        "tslib": "^2.6.2"
      }
    },
    "node_modules/@aws-crypto/util/node_modules/@smithy/is-array-buffer": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/@smithy/is-array-buffer/-/is-array-buffer-2.2.0.tgz",
      "integrity": "sha512-GGP3O9QFD24uGeAXYUjwSTXARoqpZykHadOmA8G5vfJPK0/DC67qa//0qvqrJzL1xc8WQWX7/yc7fwudjPHPhA==",
      "dependencies": {
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=14.0.0"
      }
    },
    "node_modules/@aws-crypto/util/node_modules/@smithy/util-buffer-from": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/@smithy/util-buffer-from/-/util-buffer-from-2.2.0.tgz",
      "integrity": "sha512-IJdWBbTcMQ6DA0gdNhh/BwrLkDR+ADW5Kr1aZmd4k3DIF6ezMV4R2NIAmT08wQJ3yUK82thHWmC/TnK/wpMMIA==",
      "dependencies": {
        "@smithy/is-array-buffer": "^2.2.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=14.0.0"
      }
    },
    "node_modules/@aws-crypto/util/node_modules/@smithy/util-utf8": {
      "version": "2.3.0",
      "resolved": "https://registry.npmjs.org/@smithy/util-utf8/-/util-utf8-2.3.0.tgz",
      "integrity": "sha512-R8Rdn8Hy72KKcebgLiv8jQcQkXoLMOGGv5uI1/k0l+snqkOzQ1R0ChUBCxWMlBsFMekWjq0wRudIweFs7sKT5A==",
      "dependencies": {
        "@smithy/util-buffer-from": "^2.2.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=14.0.0"
      }
    },
    "node_modules/@aws-crypto/util/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/client-cognito-identity": {
      "version": "3.685.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/client-cognito-identity/-/client-cognito-identity-3.685.0.tgz",
      "integrity": "sha512-4h+aw0pUEOVP77TpF1ec9AX0mzotsiw2alXfh+P0t+43eg2EjaKRftRpNXyt5XmUPws+wsH10uEL4CzSZo1sxQ==",
      "dependencies": {
        "@aws-crypto/sha256-browser": "5.2.0",
        "@aws-crypto/sha256-js": "5.2.0",
        "@aws-sdk/client-sso-oidc": "3.682.0",
        "@aws-sdk/client-sts": "3.682.0",
        "@aws-sdk/core": "3.679.0",
        "@aws-sdk/credential-provider-node": "3.682.0",
        "@aws-sdk/middleware-host-header": "3.679.0",
        "@aws-sdk/middleware-logger": "3.679.0",
        "@aws-sdk/middleware-recursion-detection": "3.679.0",
        "@aws-sdk/middleware-user-agent": "3.682.0",
        "@aws-sdk/region-config-resolver": "3.679.0",
        "@aws-sdk/types": "3.679.0",
        "@aws-sdk/util-endpoints": "3.679.0",
        "@aws-sdk/util-user-agent-browser": "3.679.0",
        "@aws-sdk/util-user-agent-node": "3.682.0",
        "@smithy/config-resolver": "^3.0.9",
        "@smithy/core": "^2.4.8",
        "@smithy/fetch-http-handler": "^3.2.9",
        "@smithy/hash-node": "^3.0.7",
        "@smithy/invalid-dependency": "^3.0.7",
        "@smithy/middleware-content-length": "^3.0.9",
        "@smithy/middleware-endpoint": "^3.1.4",
        "@smithy/middleware-retry": "^3.0.23",
        "@smithy/middleware-serde": "^3.0.7",
        "@smithy/middleware-stack": "^3.0.7",
        "@smithy/node-config-provider": "^3.1.8",
        "@smithy/node-http-handler": "^3.2.4",
        "@smithy/protocol-http": "^4.1.4",
        "@smithy/smithy-client": "^3.4.0",
        "@smithy/types": "^3.5.0",
        "@smithy/url-parser": "^3.0.7",
        "@smithy/util-base64": "^3.0.0",
        "@smithy/util-body-length-browser": "^3.0.0",
        "@smithy/util-body-length-node": "^3.0.0",
        "@smithy/util-defaults-mode-browser": "^3.0.23",
        "@smithy/util-defaults-mode-node": "^3.0.23",
        "@smithy/util-endpoints": "^2.1.3",
        "@smithy/util-middleware": "^3.0.7",
        "@smithy/util-retry": "^3.0.7",
        "@smithy/util-utf8": "^3.0.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/client-cognito-identity/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/client-kms": {
      "version": "3.682.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/client-kms/-/client-kms-3.682.0.tgz",
      "integrity": "sha512-4j/tCDk+oJ/Rf7dHfdBWAqgPmSVdVldwvBzvkQ+JIAdeEHnyugiRe44EtrPr8esZfVkJPogsUuytpfL4fVGTdw==",
      "dependencies": {
        "@aws-crypto/sha256-browser": "5.2.0",
        "@aws-crypto/sha256-js": "5.2.0",
        "@aws-sdk/client-sso-oidc": "3.682.0",
        "@aws-sdk/client-sts": "3.682.0",
        "@aws-sdk/core": "3.679.0",
        "@aws-sdk/credential-provider-node": "3.682.0",
        "@aws-sdk/middleware-host-header": "3.679.0",
        "@aws-sdk/middleware-logger": "3.679.0",
        "@aws-sdk/middleware-recursion-detection": "3.679.0",
        "@aws-sdk/middleware-user-agent": "3.682.0",
        "@aws-sdk/region-config-resolver": "3.679.0",
        "@aws-sdk/types": "3.679.0",
        "@aws-sdk/util-endpoints": "3.679.0",
        "@aws-sdk/util-user-agent-browser": "3.679.0",
        "@aws-sdk/util-user-agent-node": "3.682.0",
        "@smithy/config-resolver": "^3.0.9",
        "@smithy/core": "^2.4.8",
        "@smithy/fetch-http-handler": "^3.2.9",
        "@smithy/hash-node": "^3.0.7",
        "@smithy/invalid-dependency": "^3.0.7",
        "@smithy/middleware-content-length": "^3.0.9",
        "@smithy/middleware-endpoint": "^3.1.4",
        "@smithy/middleware-retry": "^3.0.23",
        "@smithy/middleware-serde": "^3.0.7",
        "@smithy/middleware-stack": "^3.0.7",
        "@smithy/node-config-provider": "^3.1.8",
        "@smithy/node-http-handler": "^3.2.4",
        "@smithy/protocol-http": "^4.1.4",
        "@smithy/smithy-client": "^3.4.0",
        "@smithy/types": "^3.5.0",
        "@smithy/url-parser": "^3.0.7",
        "@smithy/util-base64": "^3.0.0",
        "@smithy/util-body-length-browser": "^3.0.0",
        "@smithy/util-body-length-node": "^3.0.0",
        "@smithy/util-defaults-mode-browser": "^3.0.23",
        "@smithy/util-defaults-mode-node": "^3.0.23",
        "@smithy/util-endpoints": "^2.1.3",
        "@smithy/util-middleware": "^3.0.7",
        "@smithy/util-retry": "^3.0.7",
        "@smithy/util-utf8": "^3.0.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/client-kms/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/client-sso": {
      "version": "3.682.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/client-sso/-/client-sso-3.682.0.tgz",
      "integrity": "sha512-PYH9RFUMYLFl66HSBq4tIx6fHViMLkhJHTYJoJONpBs+Td+NwVJ895AdLtDsBIhMS0YseCbPpuyjUCJgsUrwUw==",
      "dependencies": {
        "@aws-crypto/sha256-browser": "5.2.0",
        "@aws-crypto/sha256-js": "5.2.0",
        "@aws-sdk/core": "3.679.0",
        "@aws-sdk/middleware-host-header": "3.679.0",
        "@aws-sdk/middleware-logger": "3.679.0",
        "@aws-sdk/middleware-recursion-detection": "3.679.0",
        "@aws-sdk/middleware-user-agent": "3.682.0",
        "@aws-sdk/region-config-resolver": "3.679.0",
        "@aws-sdk/types": "3.679.0",
        "@aws-sdk/util-endpoints": "3.679.0",
        "@aws-sdk/util-user-agent-browser": "3.679.0",
        "@aws-sdk/util-user-agent-node": "3.682.0",
        "@smithy/config-resolver": "^3.0.9",
        "@smithy/core": "^2.4.8",
        "@smithy/fetch-http-handler": "^3.2.9",
        "@smithy/hash-node": "^3.0.7",
        "@smithy/invalid-dependency": "^3.0.7",
        "@smithy/middleware-content-length": "^3.0.9",
        "@smithy/middleware-endpoint": "^3.1.4",
        "@smithy/middleware-retry": "^3.0.23",
        "@smithy/middleware-serde": "^3.0.7",
        "@smithy/middleware-stack": "^3.0.7",
        "@smithy/node-config-provider": "^3.1.8",
        "@smithy/node-http-handler": "^3.2.4",
        "@smithy/protocol-http": "^4.1.4",
        "@smithy/smithy-client": "^3.4.0",
        "@smithy/types": "^3.5.0",
        "@smithy/url-parser": "^3.0.7",
        "@smithy/util-base64": "^3.0.0",
        "@smithy/util-body-length-browser": "^3.0.0",
        "@smithy/util-body-length-node": "^3.0.0",
        "@smithy/util-defaults-mode-browser": "^3.0.23",
        "@smithy/util-defaults-mode-node": "^3.0.23",
        "@smithy/util-endpoints": "^2.1.3",
        "@smithy/util-middleware": "^3.0.7",
        "@smithy/util-retry": "^3.0.7",
        "@smithy/util-utf8": "^3.0.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/client-sso-oidc": {
      "version": "3.682.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/client-sso-oidc/-/client-sso-oidc-3.682.0.tgz",
      "integrity": "sha512-ZPZ7Y/r/w3nx/xpPzGSqSQsB090Xk5aZZOH+WBhTDn/pBEuim09BYXCLzvvxb7R7NnuoQdrTJiwimdJAhHl7ZQ==",
      "dependencies": {
        "@aws-crypto/sha256-browser": "5.2.0",
        "@aws-crypto/sha256-js": "5.2.0",
        "@aws-sdk/core": "3.679.0",
        "@aws-sdk/credential-provider-node": "3.682.0",
        "@aws-sdk/middleware-host-header": "3.679.0",
        "@aws-sdk/middleware-logger": "3.679.0",
        "@aws-sdk/middleware-recursion-detection": "3.679.0",
        "@aws-sdk/middleware-user-agent": "3.682.0",
        "@aws-sdk/region-config-resolver": "3.679.0",
        "@aws-sdk/types": "3.679.0",
        "@aws-sdk/util-endpoints": "3.679.0",
        "@aws-sdk/util-user-agent-browser": "3.679.0",
        "@aws-sdk/util-user-agent-node": "3.682.0",
        "@smithy/config-resolver": "^3.0.9",
        "@smithy/core": "^2.4.8",
        "@smithy/fetch-http-handler": "^3.2.9",
        "@smithy/hash-node": "^3.0.7",
        "@smithy/invalid-dependency": "^3.0.7",
        "@smithy/middleware-content-length": "^3.0.9",
        "@smithy/middleware-endpoint": "^3.1.4",
        "@smithy/middleware-retry": "^3.0.23",
        "@smithy/middleware-serde": "^3.0.7",
        "@smithy/middleware-stack": "^3.0.7",
        "@smithy/node-config-provider": "^3.1.8",
        "@smithy/node-http-handler": "^3.2.4",
        "@smithy/protocol-http": "^4.1.4",
        "@smithy/smithy-client": "^3.4.0",
        "@smithy/types": "^3.5.0",
        "@smithy/url-parser": "^3.0.7",
        "@smithy/util-base64": "^3.0.0",
        "@smithy/util-body-length-browser": "^3.0.0",
        "@smithy/util-body-length-node": "^3.0.0",
        "@smithy/util-defaults-mode-browser": "^3.0.23",
        "@smithy/util-defaults-mode-node": "^3.0.23",
        "@smithy/util-endpoints": "^2.1.3",
        "@smithy/util-middleware": "^3.0.7",
        "@smithy/util-retry": "^3.0.7",
        "@smithy/util-utf8": "^3.0.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      },
      "peerDependencies": {
        "@aws-sdk/client-sts": "^3.682.0"
      }
    },
    "node_modules/@aws-sdk/client-sso-oidc/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/client-sso/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/client-sts": {
      "version": "3.682.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/client-sts/-/client-sts-3.682.0.tgz",
      "integrity": "sha512-xKuo4HksZ+F8m9DOfx/ZuWNhaPuqZFPwwy0xqcBT6sWH7OAuBjv/fnpOTzyQhpVTWddlf+ECtMAMrxjxuOExGQ==",
      "dependencies": {
        "@aws-crypto/sha256-browser": "5.2.0",
        "@aws-crypto/sha256-js": "5.2.0",
        "@aws-sdk/client-sso-oidc": "3.682.0",
        "@aws-sdk/core": "3.679.0",
        "@aws-sdk/credential-provider-node": "3.682.0",
        "@aws-sdk/middleware-host-header": "3.679.0",
        "@aws-sdk/middleware-logger": "3.679.0",
        "@aws-sdk/middleware-recursion-detection": "3.679.0",
        "@aws-sdk/middleware-user-agent": "3.682.0",
        "@aws-sdk/region-config-resolver": "3.679.0",
        "@aws-sdk/types": "3.679.0",
        "@aws-sdk/util-endpoints": "3.679.0",
        "@aws-sdk/util-user-agent-browser": "3.679.0",
        "@aws-sdk/util-user-agent-node": "3.682.0",
        "@smithy/config-resolver": "^3.0.9",
        "@smithy/core": "^2.4.8",
        "@smithy/fetch-http-handler": "^3.2.9",
        "@smithy/hash-node": "^3.0.7",
        "@smithy/invalid-dependency": "^3.0.7",
        "@smithy/middleware-content-length": "^3.0.9",
        "@smithy/middleware-endpoint": "^3.1.4",
        "@smithy/middleware-retry": "^3.0.23",
        "@smithy/middleware-serde": "^3.0.7",
        "@smithy/middleware-stack": "^3.0.7",
        "@smithy/node-config-provider": "^3.1.8",
        "@smithy/node-http-handler": "^3.2.4",
        "@smithy/protocol-http": "^4.1.4",
        "@smithy/smithy-client": "^3.4.0",
        "@smithy/types": "^3.5.0",
        "@smithy/url-parser": "^3.0.7",
        "@smithy/util-base64": "^3.0.0",
        "@smithy/util-body-length-browser": "^3.0.0",
        "@smithy/util-body-length-node": "^3.0.0",
        "@smithy/util-defaults-mode-browser": "^3.0.23",
        "@smithy/util-defaults-mode-node": "^3.0.23",
        "@smithy/util-endpoints": "^2.1.3",
        "@smithy/util-middleware": "^3.0.7",
        "@smithy/util-retry": "^3.0.7",
        "@smithy/util-utf8": "^3.0.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/client-sts/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/core": {
      "version": "3.679.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/core/-/core-3.679.0.tgz",
      "integrity": "sha512-CS6PWGX8l4v/xyvX8RtXnBisdCa5+URzKd0L6GvHChype9qKUVxO/Gg6N/y43Hvg7MNWJt9FBPNWIxUB+byJwg==",
      "dependencies": {
        "@aws-sdk/types": "3.679.0",
        "@smithy/core": "^2.4.8",
        "@smithy/node-config-provider": "^3.1.8",
        "@smithy/property-provider": "^3.1.7",
        "@smithy/protocol-http": "^4.1.4",
        "@smithy/signature-v4": "^4.2.0",
        "@smithy/smithy-client": "^3.4.0",
        "@smithy/types": "^3.5.0",
        "@smithy/util-middleware": "^3.0.7",
        "fast-xml-parser": "4.4.1",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/core/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/credential-provider-cognito-identity": {
      "version": "3.685.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/credential-provider-cognito-identity/-/credential-provider-cognito-identity-3.685.0.tgz",
      "integrity": "sha512-qw9s09JFhJxEkmbo1gn94pAtyLHSx8YBX2qqrL6v3BdsJbP2fnRJMMssGMGR4jPyhklh5TSgZo0FzflbqJU8sw==",
      "dependencies": {
        "@aws-sdk/client-cognito-identity": "3.685.0",
        "@aws-sdk/types": "3.679.0",
        "@smithy/property-provider": "^3.1.7",
        "@smithy/types": "^3.5.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/credential-provider-cognito-identity/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/credential-provider-env": {
      "version": "3.679.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/credential-provider-env/-/credential-provider-env-3.679.0.tgz",
      "integrity": "sha512-EdlTYbzMm3G7VUNAMxr9S1nC1qUNqhKlAxFU8E7cKsAe8Bp29CD5HAs3POc56AVo9GC4yRIS+/mtlZSmrckzUA==",
      "dependencies": {
        "@aws-sdk/core": "3.679.0",
        "@aws-sdk/types": "3.679.0",
        "@smithy/property-provider": "^3.1.7",
        "@smithy/types": "^3.5.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/credential-provider-env/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/credential-provider-http": {
      "version": "3.679.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/credential-provider-http/-/credential-provider-http-3.679.0.tgz",
      "integrity": "sha512-ZoKLubW5DqqV1/2a3TSn+9sSKg0T8SsYMt1JeirnuLJF0mCoYFUaWMyvxxKuxPoqvUsaycxKru4GkpJ10ltNBw==",
      "dependencies": {
        "@aws-sdk/core": "3.679.0",
        "@aws-sdk/types": "3.679.0",
        "@smithy/fetch-http-handler": "^3.2.9",
        "@smithy/node-http-handler": "^3.2.4",
        "@smithy/property-provider": "^3.1.7",
        "@smithy/protocol-http": "^4.1.4",
        "@smithy/smithy-client": "^3.4.0",
        "@smithy/types": "^3.5.0",
        "@smithy/util-stream": "^3.1.9",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/credential-provider-http/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/credential-provider-ini": {
      "version": "3.682.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/credential-provider-ini/-/credential-provider-ini-3.682.0.tgz",
      "integrity": "sha512-6eqWeHdK6EegAxqDdiCi215nT3QZPwukgWAYuVxNfJ/5m0/P7fAzF+D5kKVgByUvGJEbq/FEL8Fw7OBe64AA+g==",
      "dependencies": {
        "@aws-sdk/core": "3.679.0",
        "@aws-sdk/credential-provider-env": "3.679.0",
        "@aws-sdk/credential-provider-http": "3.679.0",
        "@aws-sdk/credential-provider-process": "3.679.0",
        "@aws-sdk/credential-provider-sso": "3.682.0",
        "@aws-sdk/credential-provider-web-identity": "3.679.0",
        "@aws-sdk/types": "3.679.0",
        "@smithy/credential-provider-imds": "^3.2.4",
        "@smithy/property-provider": "^3.1.7",
        "@smithy/shared-ini-file-loader": "^3.1.8",
        "@smithy/types": "^3.5.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      },
      "peerDependencies": {
        "@aws-sdk/client-sts": "^3.682.0"
      }
    },
    "node_modules/@aws-sdk/credential-provider-ini/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/credential-provider-node": {
      "version": "3.682.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/credential-provider-node/-/credential-provider-node-3.682.0.tgz",
      "integrity": "sha512-HSmDqZcBVZrTctHCT9m++vdlDfJ1ARI218qmZa+TZzzOFNpKWy6QyHMEra45GB9GnkkMmV6unoDSPMuN0AqcMg==",
      "dependencies": {
        "@aws-sdk/credential-provider-env": "3.679.0",
        "@aws-sdk/credential-provider-http": "3.679.0",
        "@aws-sdk/credential-provider-ini": "3.682.0",
        "@aws-sdk/credential-provider-process": "3.679.0",
        "@aws-sdk/credential-provider-sso": "3.682.0",
        "@aws-sdk/credential-provider-web-identity": "3.679.0",
        "@aws-sdk/types": "3.679.0",
        "@smithy/credential-provider-imds": "^3.2.4",
        "@smithy/property-provider": "^3.1.7",
        "@smithy/shared-ini-file-loader": "^3.1.8",
        "@smithy/types": "^3.5.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/credential-provider-node/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/credential-provider-process": {
      "version": "3.679.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/credential-provider-process/-/credential-provider-process-3.679.0.tgz",
      "integrity": "sha512-u/p4TV8kQ0zJWDdZD4+vdQFTMhkDEJFws040Gm113VHa/Xo1SYOjbpvqeuFoz6VmM0bLvoOWjxB9MxnSQbwKpQ==",
      "dependencies": {
        "@aws-sdk/core": "3.679.0",
        "@aws-sdk/types": "3.679.0",
        "@smithy/property-provider": "^3.1.7",
        "@smithy/shared-ini-file-loader": "^3.1.8",
        "@smithy/types": "^3.5.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/credential-provider-process/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/credential-provider-sso": {
      "version": "3.682.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/credential-provider-sso/-/credential-provider-sso-3.682.0.tgz",
      "integrity": "sha512-h7IH1VsWgV6YAJSWWV6y8uaRjGqLY3iBpGZlXuTH/c236NMLaNv+WqCBLeBxkFGUb2WeQ+FUPEJDCD69rgLIkg==",
      "dependencies": {
        "@aws-sdk/client-sso": "3.682.0",
        "@aws-sdk/core": "3.679.0",
        "@aws-sdk/token-providers": "3.679.0",
        "@aws-sdk/types": "3.679.0",
        "@smithy/property-provider": "^3.1.7",
        "@smithy/shared-ini-file-loader": "^3.1.8",
        "@smithy/types": "^3.5.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/credential-provider-sso/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/credential-provider-web-identity": {
      "version": "3.679.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/credential-provider-web-identity/-/credential-provider-web-identity-3.679.0.tgz",
      "integrity": "sha512-a74tLccVznXCaBefWPSysUcLXYJiSkeUmQGtalNgJ1vGkE36W5l/8czFiiowdWdKWz7+x6xf0w+Kjkjlj42Ung==",
      "dependencies": {
        "@aws-sdk/core": "3.679.0",
        "@aws-sdk/types": "3.679.0",
        "@smithy/property-provider": "^3.1.7",
        "@smithy/types": "^3.5.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      },
      "peerDependencies": {
        "@aws-sdk/client-sts": "^3.679.0"
      }
    },
    "node_modules/@aws-sdk/credential-provider-web-identity/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/credential-providers": {
      "version": "3.685.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/credential-providers/-/credential-providers-3.685.0.tgz",
      "integrity": "sha512-pIXNNwPG2KnzjGYYbADquEkROuKxAJxuWt87TJO7LCFqKwb5l6h0Mc7yc4j13zxOVd/EhXD0VsPeqnobDklUoQ==",
      "dependencies": {
        "@aws-sdk/client-cognito-identity": "3.685.0",
        "@aws-sdk/client-sso": "3.682.0",
        "@aws-sdk/client-sts": "3.682.0",
        "@aws-sdk/core": "3.679.0",
        "@aws-sdk/credential-provider-cognito-identity": "3.685.0",
        "@aws-sdk/credential-provider-env": "3.679.0",
        "@aws-sdk/credential-provider-http": "3.679.0",
        "@aws-sdk/credential-provider-ini": "3.682.0",
        "@aws-sdk/credential-provider-node": "3.682.0",
        "@aws-sdk/credential-provider-process": "3.679.0",
        "@aws-sdk/credential-provider-sso": "3.682.0",
        "@aws-sdk/credential-provider-web-identity": "3.679.0",
        "@aws-sdk/types": "3.679.0",
        "@smithy/credential-provider-imds": "^3.2.4",
        "@smithy/property-provider": "^3.1.7",
        "@smithy/types": "^3.5.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/credential-providers/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/middleware-host-header": {
      "version": "3.679.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/middleware-host-header/-/middleware-host-header-3.679.0.tgz",
      "integrity": "sha512-y176HuQ8JRY3hGX8rQzHDSbCl9P5Ny9l16z4xmaiLo+Qfte7ee4Yr3yaAKd7GFoJ3/Mhud2XZ37fR015MfYl2w==",
      "dependencies": {
        "@aws-sdk/types": "3.679.0",
        "@smithy/protocol-http": "^4.1.4",
        "@smithy/types": "^3.5.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/middleware-host-header/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/middleware-logger": {
      "version": "3.679.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/middleware-logger/-/middleware-logger-3.679.0.tgz",
      "integrity": "sha512-0vet8InEj7nvIvGKk+ch7bEF5SyZ7Us9U7YTEgXPrBNStKeRUsgwRm0ijPWWd0a3oz2okaEwXsFl7G/vI0XiEA==",
      "dependencies": {
        "@aws-sdk/types": "3.679.0",
        "@smithy/types": "^3.5.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/middleware-logger/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/middleware-recursion-detection": {
      "version": "3.679.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/middleware-recursion-detection/-/middleware-recursion-detection-3.679.0.tgz",
      "integrity": "sha512-sQoAZFsQiW/LL3DfKMYwBoGjYDEnMbA9WslWN8xneCmBAwKo6IcSksvYs23PP8XMIoBGe2I2J9BSr654XWygTQ==",
      "dependencies": {
        "@aws-sdk/types": "3.679.0",
        "@smithy/protocol-http": "^4.1.4",
        "@smithy/types": "^3.5.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/middleware-recursion-detection/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/middleware-user-agent": {
      "version": "3.682.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/middleware-user-agent/-/middleware-user-agent-3.682.0.tgz",
      "integrity": "sha512-7TyvYR9HdGH1/Nq0eeApUTM4izB6rExiw87khVYuJwZHr6FmvIL1FsOVFro/4WlXa0lg4LiYOm/8H8dHv+fXTg==",
      "dependencies": {
        "@aws-sdk/core": "3.679.0",
        "@aws-sdk/types": "3.679.0",
        "@aws-sdk/util-endpoints": "3.679.0",
        "@smithy/core": "^2.4.8",
        "@smithy/protocol-http": "^4.1.4",
        "@smithy/types": "^3.5.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/middleware-user-agent/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/region-config-resolver": {
      "version": "3.679.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/region-config-resolver/-/region-config-resolver-3.679.0.tgz",
      "integrity": "sha512-Ybx54P8Tg6KKq5ck7uwdjiKif7n/8g1x+V0V9uTjBjRWqaIgiqzXwKWoPj6NCNkE7tJNtqI4JrNxp/3S3HvmRw==",
      "dependencies": {
        "@aws-sdk/types": "3.679.0",
        "@smithy/node-config-provider": "^3.1.8",
        "@smithy/types": "^3.5.0",
        "@smithy/util-config-provider": "^3.0.0",
        "@smithy/util-middleware": "^3.0.7",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/region-config-resolver/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/token-providers": {
      "version": "3.679.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/token-providers/-/token-providers-3.679.0.tgz",
      "integrity": "sha512-1/+Zso/x2jqgutKixYFQEGli0FELTgah6bm7aB+m2FAWH4Hz7+iMUsazg6nSWm714sG9G3h5u42Dmpvi9X6/hA==",
      "dependencies": {
        "@aws-sdk/types": "3.679.0",
        "@smithy/property-provider": "^3.1.7",
        "@smithy/shared-ini-file-loader": "^3.1.8",
        "@smithy/types": "^3.5.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      },
      "peerDependencies": {
        "@aws-sdk/client-sso-oidc": "^3.679.0"
      }
    },
    "node_modules/@aws-sdk/token-providers/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/types": {
      "version": "3.679.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/types/-/types-3.679.0.tgz",
      "integrity": "sha512-NwVq8YvInxQdJ47+zz4fH3BRRLC6lL+WLkvr242PVBbUOLRyK/lkwHlfiKUoeVIMyK5NF+up6TRg71t/8Bny6Q==",
      "dependencies": {
        "@smithy/types": "^3.5.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/types/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/util-endpoints": {
      "version": "3.679.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/util-endpoints/-/util-endpoints-3.679.0.tgz",
      "integrity": "sha512-YL6s4Y/1zC45OvddvgE139fjeWSKKPgLlnfrvhVL7alNyY9n7beR4uhoDpNrt5mI6sn9qiBF17790o+xLAXjjg==",
      "dependencies": {
        "@aws-sdk/types": "3.679.0",
        "@smithy/types": "^3.5.0",
        "@smithy/util-endpoints": "^2.1.3",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/util-endpoints/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/util-locate-window": {
      "version": "3.679.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/util-locate-window/-/util-locate-window-3.679.0.tgz",
      "integrity": "sha512-zKTd48/ZWrCplkXpYDABI74rQlbR0DNHs8nH95htfSLj9/mWRSwaGptoxwcihaq/77vi/fl2X3y0a1Bo8bt7RA==",
      "dependencies": {
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@aws-sdk/util-locate-window/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/util-user-agent-browser": {
      "version": "3.679.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/util-user-agent-browser/-/util-user-agent-browser-3.679.0.tgz",
      "integrity": "sha512-CusSm2bTBG1kFypcsqU8COhnYc6zltobsqs3nRrvYqYaOqtMnuE46K4XTWpnzKgwDejgZGOE+WYyprtAxrPvmQ==",
      "dependencies": {
        "@aws-sdk/types": "3.679.0",
        "@smithy/types": "^3.5.0",
        "bowser": "^2.11.0",
        "tslib": "^2.6.2"
      }
    },
    "node_modules/@aws-sdk/util-user-agent-browser/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@aws-sdk/util-user-agent-node": {
      "version": "3.682.0",
      "resolved": "https://registry.npmjs.org/@aws-sdk/util-user-agent-node/-/util-user-agent-node-3.682.0.tgz",
      "integrity": "sha512-so5s+j0gPoTS0HM4HPL+G0ajk0T6cQAg8JXzRgvyiQAxqie+zGCZAV3VuVeMNWMVbzsgZl0pYZaatPFTLG/AxA==",
      "dependencies": {
        "@aws-sdk/middleware-user-agent": "3.682.0",
        "@aws-sdk/types": "3.679.0",
        "@smithy/node-config-provider": "^3.1.8",
        "@smithy/types": "^3.5.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      },
      "peerDependencies": {
        "aws-crt": ">=1.0.0"
      },
      "peerDependenciesMeta": {
        "aws-crt": {
          "optional": true
        }
      }
    },
    "node_modules/@aws-sdk/util-user-agent-node/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@babel/code-frame": {
      "version": "7.26.2",
      "resolved": "https://registry.npmjs.org/@babel/code-frame/-/code-frame-7.26.2.tgz",
      "integrity": "sha512-RJlIHRueQgwWitWgF8OdFYGZX328Ax5BCemNGlqHfplnRT9ESi8JkFlvaVYbS+UubVY6dpv87Fs2u5M29iNFVQ==",
      "dev": true,
      "dependencies": {
        "@babel/helper-validator-identifier": "^7.25.9",
        "js-tokens": "^4.0.0",
        "picocolors": "^1.0.0"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/compat-data": {
      "version": "7.26.2",
      "resolved": "https://registry.npmjs.org/@babel/compat-data/-/compat-data-7.26.2.tgz",
      "integrity": "sha512-Z0WgzSEa+aUcdiJuCIqgujCshpMWgUpgOxXotrYPSA53hA3qopNaqcJpyr0hVb1FeWdnqFA35/fUtXgBK8srQg==",
      "dev": true,
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/core": {
      "version": "7.26.0",
      "resolved": "https://registry.npmjs.org/@babel/core/-/core-7.26.0.tgz",
      "integrity": "sha512-i1SLeK+DzNnQ3LL/CswPCa/E5u4lh1k6IAEphON8F+cXt0t9euTshDru0q7/IqMa1PMPz5RnHuHscF8/ZJsStg==",
      "dev": true,
      "dependencies": {
        "@ampproject/remapping": "^2.2.0",
        "@babel/code-frame": "^7.26.0",
        "@babel/generator": "^7.26.0",
        "@babel/helper-compilation-targets": "^7.25.9",
        "@babel/helper-module-transforms": "^7.26.0",
        "@babel/helpers": "^7.26.0",
        "@babel/parser": "^7.26.0",
        "@babel/template": "^7.25.9",
        "@babel/traverse": "^7.25.9",
        "@babel/types": "^7.26.0",
        "convert-source-map": "^2.0.0",
        "debug": "^4.1.0",
        "gensync": "^1.0.0-beta.2",
        "json5": "^2.2.3",
        "semver": "^6.3.1"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/babel"
      }
    },
    "node_modules/@babel/core/node_modules/semver": {
      "version": "6.3.1",
      "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.1.tgz",
      "integrity": "sha512-BR7VvDCVHO+q2xBEWskxS6DJE1qRnb7DxzUrogb71CWoSficBxYsiAGd+Kl0mmq/MprG9yArRkyrQxTO6XjMzA==",
      "dev": true,
      "bin": {
        "semver": "bin/semver.js"
      }
    },
    "node_modules/@babel/generator": {
      "version": "7.26.2",
      "resolved": "https://registry.npmjs.org/@babel/generator/-/generator-7.26.2.tgz",
      "integrity": "sha512-zevQbhbau95nkoxSq3f/DC/SC+EEOUZd3DYqfSkMhY2/wfSeaHV1Ew4vk8e+x8lja31IbyuUa2uQ3JONqKbysw==",
      "dev": true,
      "dependencies": {
        "@babel/parser": "^7.26.2",
        "@babel/types": "^7.26.0",
        "@jridgewell/gen-mapping": "^0.3.5",
        "@jridgewell/trace-mapping": "^0.3.25",
        "jsesc": "^3.0.2"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-compilation-targets": {
      "version": "7.25.9",
      "resolved": "https://registry.npmjs.org/@babel/helper-compilation-targets/-/helper-compilation-targets-7.25.9.tgz",
      "integrity": "sha512-j9Db8Suy6yV/VHa4qzrj9yZfZxhLWQdVnRlXxmKLYlhWUVB1sB2G5sxuWYXk/whHD9iW76PmNzxZ4UCnTQTVEQ==",
      "dev": true,
      "dependencies": {
        "@babel/compat-data": "^7.25.9",
        "@babel/helper-validator-option": "^7.25.9",
        "browserslist": "^4.24.0",
        "lru-cache": "^5.1.1",
        "semver": "^6.3.1"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-compilation-targets/node_modules/semver": {
      "version": "6.3.1",
      "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.1.tgz",
      "integrity": "sha512-BR7VvDCVHO+q2xBEWskxS6DJE1qRnb7DxzUrogb71CWoSficBxYsiAGd+Kl0mmq/MprG9yArRkyrQxTO6XjMzA==",
      "dev": true,
      "bin": {
        "semver": "bin/semver.js"
      }
    },
    "node_modules/@babel/helper-module-imports": {
      "version": "7.25.9",
      "resolved": "https://registry.npmjs.org/@babel/helper-module-imports/-/helper-module-imports-7.25.9.tgz",
      "integrity": "sha512-tnUA4RsrmflIM6W6RFTLFSXITtl0wKjgpnLgXyowocVPrbYrLUXSBXDgTs8BlbmIzIdlBySRQjINYs2BAkiLtw==",
      "dev": true,
      "dependencies": {
        "@babel/traverse": "^7.25.9",
        "@babel/types": "^7.25.9"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-module-transforms": {
      "version": "7.26.0",
      "resolved": "https://registry.npmjs.org/@babel/helper-module-transforms/-/helper-module-transforms-7.26.0.tgz",
      "integrity": "sha512-xO+xu6B5K2czEnQye6BHA7DolFFmS3LB7stHZFaOLb1pAwO1HWLS8fXA+eh0A2yIvltPVmx3eNNDBJA2SLHXFw==",
      "dev": true,
      "dependencies": {
        "@babel/helper-module-imports": "^7.25.9",
        "@babel/helper-validator-identifier": "^7.25.9",
        "@babel/traverse": "^7.25.9"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0"
      }
    },
    "node_modules/@babel/helper-plugin-utils": {
      "version": "7.25.9",
      "resolved": "https://registry.npmjs.org/@babel/helper-plugin-utils/-/helper-plugin-utils-7.25.9.tgz",
      "integrity": "sha512-kSMlyUVdWe25rEsRGviIgOWnoT/nfABVWlqt9N19/dIPWViAOW2s9wznP5tURbs/IDuNk4gPy3YdYRgH3uxhBw==",
      "dev": true,
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-string-parser": {
      "version": "7.25.9",
      "resolved": "https://registry.npmjs.org/@babel/helper-string-parser/-/helper-string-parser-7.25.9.tgz",
      "integrity": "sha512-4A/SCr/2KLd5jrtOMFzaKjVtAei3+2r/NChoBNoZ3EyP/+GlhoaEGoWOZUmFmoITP7zOJyHIMm+DYRd8o3PvHA==",
      "dev": true,
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-validator-identifier": {
      "version": "7.25.9",
      "resolved": "https://registry.npmjs.org/@babel/helper-validator-identifier/-/helper-validator-identifier-7.25.9.tgz",
      "integrity": "sha512-Ed61U6XJc3CVRfkERJWDz4dJwKe7iLmmJsbOGu9wSloNSFttHV0I8g6UAgb7qnK5ly5bGLPd4oXZlxCdANBOWQ==",
      "dev": true,
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-validator-option": {
      "version": "7.25.9",
      "resolved": "https://registry.npmjs.org/@babel/helper-validator-option/-/helper-validator-option-7.25.9.tgz",
      "integrity": "sha512-e/zv1co8pp55dNdEcCynfj9X7nyUKUXoUEwfXqaZt0omVOmDe9oOTdKStH4GmAw6zxMFs50ZayuMfHDKlO7Tfw==",
      "dev": true,
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helpers": {
      "version": "7.26.0",
      "resolved": "https://registry.npmjs.org/@babel/helpers/-/helpers-7.26.0.tgz",
      "integrity": "sha512-tbhNuIxNcVb21pInl3ZSjksLCvgdZy9KwJ8brv993QtIVKJBBkYXz4q4ZbAv31GdnC+R90np23L5FbEBlthAEw==",
      "dev": true,
      "dependencies": {
        "@babel/template": "^7.25.9",
        "@babel/types": "^7.26.0"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/parser": {
      "version": "7.26.2",
      "resolved": "https://registry.npmjs.org/@babel/parser/-/parser-7.26.2.tgz",
      "integrity": "sha512-DWMCZH9WA4Maitz2q21SRKHo9QXZxkDsbNZoVD62gusNtNBBqDg9i7uOhASfTfIGNzW+O+r7+jAlM8dwphcJKQ==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.26.0"
      },
      "bin": {
        "parser": "bin/babel-parser.js"
      },
      "engines": {
        "node": ">=6.0.0"
      }
    },
    "node_modules/@babel/plugin-transform-react-jsx-self": {
      "version": "7.25.9",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-react-jsx-self/-/plugin-transform-react-jsx-self-7.25.9.tgz",
      "integrity": "sha512-y8quW6p0WHkEhmErnfe58r7x0A70uKphQm8Sp8cV7tjNQwK56sNVK0M73LK3WuYmsuyrftut4xAkjjgU0twaMg==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.25.9"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-react-jsx-source": {
      "version": "7.25.9",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-react-jsx-source/-/plugin-transform-react-jsx-source-7.25.9.tgz",
      "integrity": "sha512-+iqjT8xmXhhYv4/uiYd8FNQsraMFZIfxVSqxxVSZP0WbbSAWvBXAul0m/zu+7Vv4O/3WtApy9pmaTMiumEZgfg==",
      "dev": true,
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.25.9"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/runtime": {
      "version": "7.26.0",
      "resolved": "https://registry.npmjs.org/@babel/runtime/-/runtime-7.26.0.tgz",
      "integrity": "sha512-FDSOghenHTiToteC/QRlv2q3DhPZ/oOXTBoirfWNx1Cx3TMVcGWQtMMmQcSvb/JjpNeGzx8Pq/b4fKEJuWm1sw==",
      "dependencies": {
        "regenerator-runtime": "^0.14.0"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/template": {
      "version": "7.25.9",
      "resolved": "https://registry.npmjs.org/@babel/template/-/template-7.25.9.tgz",
      "integrity": "sha512-9DGttpmPvIxBb/2uwpVo3dqJ+O6RooAFOS+lB+xDqoE2PVCE8nfoHMdZLpfCQRLwvohzXISPZcgxt80xLfsuwg==",
      "dev": true,
      "dependencies": {
        "@babel/code-frame": "^7.25.9",
        "@babel/parser": "^7.25.9",
        "@babel/types": "^7.25.9"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/traverse": {
      "version": "7.25.9",
      "resolved": "https://registry.npmjs.org/@babel/traverse/-/traverse-7.25.9.tgz",
      "integrity": "sha512-ZCuvfwOwlz/bawvAuvcj8rrithP2/N55Tzz342AkTvq4qaWbGfmCk/tKhNaV2cthijKrPAA8SRJV5WWe7IBMJw==",
      "dev": true,
      "dependencies": {
        "@babel/code-frame": "^7.25.9",
        "@babel/generator": "^7.25.9",
        "@babel/parser": "^7.25.9",
        "@babel/template": "^7.25.9",
        "@babel/types": "^7.25.9",
        "debug": "^4.3.1",
        "globals": "^11.1.0"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/types": {
      "version": "7.26.0",
      "resolved": "https://registry.npmjs.org/@babel/types/-/types-7.26.0.tgz",
      "integrity": "sha512-Z/yiTPj+lDVnF7lWeKCIJzaIkI0vYO87dMpZ4bg4TDrFe4XXLFWL1TbXU27gBP3QccxV9mZICCrnjnYlJjXHOA==",
      "dev": true,
      "dependencies": {
        "@babel/helper-string-parser": "^7.25.9",
        "@babel/helper-validator-identifier": "^7.25.9"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@coinbase/wallet-sdk": {
      "version": "3.9.3",
      "resolved": "https://registry.npmjs.org/@coinbase/wallet-sdk/-/wallet-sdk-3.9.3.tgz",
      "integrity": "sha512-N/A2DRIf0Y3PHc1XAMvbBUu4zisna6qAdqABMZwBMNEfWrXpAwx16pZGkYCLGE+Rvv1edbcB2LYDRnACNcmCiw==",
      "dependencies": {
        "bn.js": "^5.2.1",
        "buffer": "^6.0.3",
        "clsx": "^1.2.1",
        "eth-block-tracker": "^7.1.0",
        "eth-json-rpc-filters": "^6.0.0",
        "eventemitter3": "^5.0.1",
        "keccak": "^3.0.3",
        "preact": "^10.16.0",
        "sha.js": "^2.4.11"
      }
    },
    "node_modules/@coinbase/wallet-sdk/node_modules/eventemitter3": {
      "version": "5.0.1",
      "resolved": "https://registry.npmjs.org/eventemitter3/-/eventemitter3-5.0.1.tgz",
      "integrity": "sha512-GWkBvjiSZK87ELrYOSESUYeVIc9mvLLf/nXalMOS5dYrgZq9o5OVkbZAVM06CVxYsCwH9BDZFPlQTlPA1j4ahA=="
    },
    "node_modules/@ctrl/tinycolor": {
      "version": "3.6.1",
      "resolved": "https://registry.npmjs.org/@ctrl/tinycolor/-/tinycolor-3.6.1.tgz",
      "integrity": "sha512-SITSV6aIXsuVNV3f3O0f2n/cgyEDWoSqtZMYiAmcsYHydcKrOz3gUxB/iXd/Qf08+IZX4KpgNbvUdMBmWz+kcA==",
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/@esbuild/aix-ppc64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/aix-ppc64/-/aix-ppc64-0.21.5.tgz",
      "integrity": "sha512-1SDgH6ZSPTlggy1yI6+Dbkiz8xzpHJEVAlF/AM1tHPLsf5STom9rwtjE4hKAF20FfXXNTFqEYXyJNWh1GiZedQ==",
      "cpu": [
        "ppc64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "aix"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/android-arm": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/android-arm/-/android-arm-0.21.5.tgz",
      "integrity": "sha512-vCPvzSjpPHEi1siZdlvAlsPxXl7WbOVUBBAowWug4rJHb68Ox8KualB+1ocNvT5fjv6wpkX6o/iEpbDrf68zcg==",
      "cpu": [
        "arm"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "android"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/android-arm64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/android-arm64/-/android-arm64-0.21.5.tgz",
      "integrity": "sha512-c0uX9VAUBQ7dTDCjq+wdyGLowMdtR/GoC2U5IYk/7D1H1JYC0qseD7+11iMP2mRLN9RcCMRcjC4YMclCzGwS/A==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "android"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/android-x64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/android-x64/-/android-x64-0.21.5.tgz",
      "integrity": "sha512-D7aPRUUNHRBwHxzxRvp856rjUHRFW1SdQATKXH2hqA0kAZb1hKmi02OpYRacl0TxIGz/ZmXWlbZgjwWYaCakTA==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "android"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/darwin-arm64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/darwin-arm64/-/darwin-arm64-0.21.5.tgz",
      "integrity": "sha512-DwqXqZyuk5AiWWf3UfLiRDJ5EDd49zg6O9wclZ7kUMv2WRFr4HKjXp/5t8JZ11QbQfUS6/cRCKGwYhtNAY88kQ==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "darwin"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/darwin-x64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/darwin-x64/-/darwin-x64-0.21.5.tgz",
      "integrity": "sha512-se/JjF8NlmKVG4kNIuyWMV/22ZaerB+qaSi5MdrXtd6R08kvs2qCN4C09miupktDitvh8jRFflwGFBQcxZRjbw==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "darwin"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/freebsd-arm64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/freebsd-arm64/-/freebsd-arm64-0.21.5.tgz",
      "integrity": "sha512-5JcRxxRDUJLX8JXp/wcBCy3pENnCgBR9bN6JsY4OmhfUtIHe3ZW0mawA7+RDAcMLrMIZaf03NlQiX9DGyB8h4g==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "freebsd"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/freebsd-x64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/freebsd-x64/-/freebsd-x64-0.21.5.tgz",
      "integrity": "sha512-J95kNBj1zkbMXtHVH29bBriQygMXqoVQOQYA+ISs0/2l3T9/kj42ow2mpqerRBxDJnmkUDCaQT/dfNXWX/ZZCQ==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "freebsd"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-arm": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-arm/-/linux-arm-0.21.5.tgz",
      "integrity": "sha512-bPb5AHZtbeNGjCKVZ9UGqGwo8EUu4cLq68E95A53KlxAPRmUyYv2D6F0uUI65XisGOL1hBP5mTronbgo+0bFcA==",
      "cpu": [
        "arm"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-arm64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-arm64/-/linux-arm64-0.21.5.tgz",
      "integrity": "sha512-ibKvmyYzKsBeX8d8I7MH/TMfWDXBF3db4qM6sy+7re0YXya+K1cem3on9XgdT2EQGMu4hQyZhan7TeQ8XkGp4Q==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-ia32": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-ia32/-/linux-ia32-0.21.5.tgz",
      "integrity": "sha512-YvjXDqLRqPDl2dvRODYmmhz4rPeVKYvppfGYKSNGdyZkA01046pLWyRKKI3ax8fbJoK5QbxblURkwK/MWY18Tg==",
      "cpu": [
        "ia32"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-loong64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-loong64/-/linux-loong64-0.21.5.tgz",
      "integrity": "sha512-uHf1BmMG8qEvzdrzAqg2SIG/02+4/DHB6a9Kbya0XDvwDEKCoC8ZRWI5JJvNdUjtciBGFQ5PuBlpEOXQj+JQSg==",
      "cpu": [
        "loong64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-mips64el": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-mips64el/-/linux-mips64el-0.21.5.tgz",
      "integrity": "sha512-IajOmO+KJK23bj52dFSNCMsz1QP1DqM6cwLUv3W1QwyxkyIWecfafnI555fvSGqEKwjMXVLokcV5ygHW5b3Jbg==",
      "cpu": [
        "mips64el"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-ppc64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-ppc64/-/linux-ppc64-0.21.5.tgz",
      "integrity": "sha512-1hHV/Z4OEfMwpLO8rp7CvlhBDnjsC3CttJXIhBi+5Aj5r+MBvy4egg7wCbe//hSsT+RvDAG7s81tAvpL2XAE4w==",
      "cpu": [
        "ppc64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-riscv64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-riscv64/-/linux-riscv64-0.21.5.tgz",
      "integrity": "sha512-2HdXDMd9GMgTGrPWnJzP2ALSokE/0O5HhTUvWIbD3YdjME8JwvSCnNGBnTThKGEB91OZhzrJ4qIIxk/SBmyDDA==",
      "cpu": [
        "riscv64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-s390x": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-s390x/-/linux-s390x-0.21.5.tgz",
      "integrity": "sha512-zus5sxzqBJD3eXxwvjN1yQkRepANgxE9lgOW2qLnmr8ikMTphkjgXu1HR01K4FJg8h1kEEDAqDcZQtbrRnB41A==",
      "cpu": [
        "s390x"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-x64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-x64/-/linux-x64-0.21.5.tgz",
      "integrity": "sha512-1rYdTpyv03iycF1+BhzrzQJCdOuAOtaqHTWJZCWvijKD2N5Xu0TtVC8/+1faWqcP9iBCWOmjmhoH94dH82BxPQ==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/netbsd-x64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/netbsd-x64/-/netbsd-x64-0.21.5.tgz",
      "integrity": "sha512-Woi2MXzXjMULccIwMnLciyZH4nCIMpWQAs049KEeMvOcNADVxo0UBIQPfSmxB3CWKedngg7sWZdLvLczpe0tLg==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "netbsd"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/openbsd-x64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/openbsd-x64/-/openbsd-x64-0.21.5.tgz",
      "integrity": "sha512-HLNNw99xsvx12lFBUwoT8EVCsSvRNDVxNpjZ7bPn947b8gJPzeHWyNVhFsaerc0n3TsbOINvRP2byTZ5LKezow==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "openbsd"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/sunos-x64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/sunos-x64/-/sunos-x64-0.21.5.tgz",
      "integrity": "sha512-6+gjmFpfy0BHU5Tpptkuh8+uw3mnrvgs+dSPQXQOv3ekbordwnzTVEb4qnIvQcYXq6gzkyTnoZ9dZG+D4garKg==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "sunos"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/win32-arm64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/win32-arm64/-/win32-arm64-0.21.5.tgz",
      "integrity": "sha512-Z0gOTd75VvXqyq7nsl93zwahcTROgqvuAcYDUr+vOv8uHhNSKROyU961kgtCD1e95IqPKSQKH7tBTslnS3tA8A==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "win32"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/win32-ia32": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/win32-ia32/-/win32-ia32-0.21.5.tgz",
      "integrity": "sha512-SWXFF1CL2RVNMaVs+BBClwtfZSvDgtL//G/smwAc5oVK/UPu2Gu9tIaRgFmYFFKrmg3SyAjSrElf0TiJ1v8fYA==",
      "cpu": [
        "ia32"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "win32"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/win32-x64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/win32-x64/-/win32-x64-0.21.5.tgz",
      "integrity": "sha512-tQd/1efJuzPC6rCFwEvLtci/xNFcTZknmXs98FYDfGE4wP9ClFV98nyKrzJKVPMhdDnjzLhdUyMX4PsQAPjwIw==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "win32"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@eslint-community/eslint-utils": {
      "version": "4.4.1",
      "resolved": "https://registry.npmjs.org/@eslint-community/eslint-utils/-/eslint-utils-4.4.1.tgz",
      "integrity": "sha512-s3O3waFUrMV8P/XaF/+ZTp1X9XBZW1a4B97ZnjQF2KYWaFD2A8KyFBsrsfSjEmjn3RGWAIuvlneuZm3CUK3jbA==",
      "dev": true,
      "dependencies": {
        "eslint-visitor-keys": "^3.4.3"
      },
      "engines": {
        "node": "^12.22.0 || ^14.17.0 || >=16.0.0"
      },
      "funding": {
        "url": "https://opencollective.com/eslint"
      },
      "peerDependencies": {
        "eslint": "^6.0.0 || ^7.0.0 || >=8.0.0"
      }
    },
    "node_modules/@eslint-community/regexpp": {
      "version": "4.12.1",
      "resolved": "https://registry.npmjs.org/@eslint-community/regexpp/-/regexpp-4.12.1.tgz",
      "integrity": "sha512-CCZCDJuduB9OUkFkY2IgppNZMi2lBQgD2qzwXkEia16cge2pijY/aXi96CJMquDMn3nJdlPV1A5KrJEXwfLNzQ==",
      "dev": true,
      "engines": {
        "node": "^12.0.0 || ^14.0.0 || >=16.0.0"
      }
    },
    "node_modules/@eslint/eslintrc": {
      "version": "2.1.4",
      "resolved": "https://registry.npmjs.org/@eslint/eslintrc/-/eslintrc-2.1.4.tgz",
      "integrity": "sha512-269Z39MS6wVJtsoUl10L60WdkhJVdPG24Q4eZTH3nnF6lpvSShEK3wQjDX9JRWAUPvPh7COouPpU9IrqaZFvtQ==",
      "dev": true,
      "dependencies": {
        "ajv": "^6.12.4",
        "debug": "^4.3.2",
        "espree": "^9.6.0",
        "globals": "^13.19.0",
        "ignore": "^5.2.0",
        "import-fresh": "^3.2.1",
        "js-yaml": "^4.1.0",
        "minimatch": "^3.1.2",
        "strip-json-comments": "^3.1.1"
      },
      "engines": {
        "node": "^12.22.0 || ^14.17.0 || >=16.0.0"
      },
      "funding": {
        "url": "https://opencollective.com/eslint"
      }
    },
    "node_modules/@eslint/eslintrc/node_modules/brace-expansion": {
      "version": "1.1.11",
      "resolved": "https://registry.npmjs.org/brace-expansion/-/brace-expansion-1.1.11.tgz",
      "integrity": "sha512-iCuPHDFgrHX7H2vEI/5xpz07zSHB00TpugqhmYtVmMO6518mCuRMoOYFldEBl0g187ufozdaHgWKcYFb61qGiA==",
      "dev": true,
      "dependencies": {
        "balanced-match": "^1.0.0",
        "concat-map": "0.0.1"
      }
    },
    "node_modules/@eslint/eslintrc/node_modules/globals": {
      "version": "13.24.0",
      "resolved": "https://registry.npmjs.org/globals/-/globals-13.24.0.tgz",
      "integrity": "sha512-AhO5QUcj8llrbG09iWhPU2B204J1xnPeL8kQmVorSsy+Sjj1sk8gIyh6cUocGmH4L0UuhAJy+hJMRA4mgA4mFQ==",
      "dev": true,
      "dependencies": {
        "type-fest": "^0.20.2"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/@eslint/eslintrc/node_modules/minimatch": {
      "version": "3.1.2",
      "resolved": "https://registry.npmjs.org/minimatch/-/minimatch-3.1.2.tgz",
      "integrity": "sha512-J7p63hRiAjw1NDEww1W7i37+ByIrOWO5XQQAzZ3VOcL0PNybwpfmV/N05zFAzwQ9USyEcX6t3UO+K5aqBQOIHw==",
      "dev": true,
      "dependencies": {
        "brace-expansion": "^1.1.7"
      },
      "engines": {
        "node": "*"
      }
    },
    "node_modules/@eslint/js": {
      "version": "8.57.1",
      "resolved": "https://registry.npmjs.org/@eslint/js/-/js-8.57.1.tgz",
      "integrity": "sha512-d9zaMRSTIKDLhctzH12MtXvJKSSUhaHcjV+2Z+GK+EEY7XKpP5yR4x+N3TAcHTcu963nIr+TMcCb4DBCYX1z6Q==",
      "dev": true,
      "engines": {
        "node": "^12.22.0 || ^14.17.0 || >=16.0.0"
      }
    },
    "node_modules/@ethereumjs/common": {
      "version": "3.2.0",
      "resolved": "https://registry.npmjs.org/@ethereumjs/common/-/common-3.2.0.tgz",
      "integrity": "sha512-pksvzI0VyLgmuEF2FA/JR/4/y6hcPq8OUail3/AvycBaW1d5VSauOZzqGvJ3RTmR4MU35lWE8KseKOsEhrFRBA==",
      "dependencies": {
        "@ethereumjs/util": "^8.1.0",
        "crc-32": "^1.2.0"
      }
    },
    "node_modules/@ethereumjs/rlp": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/@ethereumjs/rlp/-/rlp-4.0.1.tgz",
      "integrity": "sha512-tqsQiBQDQdmPWE1xkkBq4rlSW5QZpLOUJ5RJh2/9fug+q9tnUhuZoVLk7s0scUIKTOzEtR72DFBXI4WiZcMpvw==",
      "bin": {
        "rlp": "bin/rlp"
      },
      "engines": {
        "node": ">=14"
      }
    },
    "node_modules/@ethereumjs/tx": {
      "version": "4.2.0",
      "resolved": "https://registry.npmjs.org/@ethereumjs/tx/-/tx-4.2.0.tgz",
      "integrity": "sha512-1nc6VO4jtFd172BbSnTnDQVr9IYBFl1y4xPzZdtkrkKIncBCkdbgfdRV+MiTkJYAtTxvV12GRZLqBFT1PNK6Yw==",
      "dependencies": {
        "@ethereumjs/common": "^3.2.0",
        "@ethereumjs/rlp": "^4.0.1",
        "@ethereumjs/util": "^8.1.0",
        "ethereum-cryptography": "^2.0.0"
      },
      "engines": {
        "node": ">=14"
      }
    },
    "node_modules/@ethereumjs/util": {
      "version": "8.1.0",
      "resolved": "https://registry.npmjs.org/@ethereumjs/util/-/util-8.1.0.tgz",
      "integrity": "sha512-zQ0IqbdX8FZ9aw11vP+dZkKDkS+kgIvQPHnSAXzP9pLu+Rfu3D3XEeLbicvoXJTYnhZiPmsZUxgdzXwNKxRPbA==",
      "dependencies": {
        "@ethereumjs/rlp": "^4.0.1",
        "ethereum-cryptography": "^2.0.0",
        "micro-ftch": "^0.3.1"
      },
      "engines": {
        "node": ">=14"
      }
    },
    "node_modules/@ethersproject/bignumber": {
      "version": "5.7.0",
      "resolved": "https://registry.npmjs.org/@ethersproject/bignumber/-/bignumber-5.7.0.tgz",
      "integrity": "sha512-n1CAdIHRWjSucQO3MC1zPSVgV/6dy/fjL9pMrPP9peL+QxEg9wOsVqwD4+818B6LUEtaXzVHQiuivzRoxPxUGw==",
      "funding": [
        {
          "type": "individual",
          "url": "https://gitcoin.co/grants/13/ethersjs-complete-simple-and-tiny-2"
        },
        {
          "type": "individual",
          "url": "https://www.buymeacoffee.com/ricmoo"
        }
      ],
      "dependencies": {
        "@ethersproject/bytes": "^5.7.0",
        "@ethersproject/logger": "^5.7.0",
        "bn.js": "^5.2.1"
      }
    },
    "node_modules/@ethersproject/bytes": {
      "version": "5.7.0",
      "resolved": "https://registry.npmjs.org/@ethersproject/bytes/-/bytes-5.7.0.tgz",
      "integrity": "sha512-nsbxwgFXWh9NyYWo+U8atvmMsSdKJprTcICAkvbBffT75qDocbuggBU0SJiVK2MuTrp0q+xvLkTnGMPK1+uA9A==",
      "funding": [
        {
          "type": "individual",
          "url": "https://gitcoin.co/grants/13/ethersjs-complete-simple-and-tiny-2"
        },
        {
          "type": "individual",
          "url": "https://www.buymeacoffee.com/ricmoo"
        }
      ],
      "dependencies": {
        "@ethersproject/logger": "^5.7.0"
      }
    },
    "node_modules/@ethersproject/constants": {
      "version": "5.7.0",
      "resolved": "https://registry.npmjs.org/@ethersproject/constants/-/constants-5.7.0.tgz",
      "integrity": "sha512-DHI+y5dBNvkpYUMiRQyxRBYBefZkJfo70VUkUAsRjcPs47muV9evftfZ0PJVCXYbAiCgght0DtcF9srFQmIgWA==",
      "funding": [
        {
          "type": "individual",
          "url": "https://gitcoin.co/grants/13/ethersjs-complete-simple-and-tiny-2"
        },
        {
          "type": "individual",
          "url": "https://www.buymeacoffee.com/ricmoo"
        }
      ],
      "dependencies": {
        "@ethersproject/bignumber": "^5.7.0"
      }
    },
    "node_modules/@ethersproject/logger": {
      "version": "5.7.0",
      "resolved": "https://registry.npmjs.org/@ethersproject/logger/-/logger-5.7.0.tgz",
      "integrity": "sha512-0odtFdXu/XHtjQXJYA3u9G0G8btm0ND5Cu8M7i5vhEcE8/HmF4Lbdqanwyv4uQTr2tx6b7fQRmgLrsnpQlmnig==",
      "funding": [
        {
          "type": "individual",
          "url": "https://gitcoin.co/grants/13/ethersjs-complete-simple-and-tiny-2"
        },
        {
          "type": "individual",
          "url": "https://www.buymeacoffee.com/ricmoo"
        }
      ]
    },
    "node_modules/@ethersproject/units": {
      "version": "5.7.0",
      "resolved": "https://registry.npmjs.org/@ethersproject/units/-/units-5.7.0.tgz",
      "integrity": "sha512-pD3xLMy3SJu9kG5xDGI7+xhTEmGXlEqXU4OfNapmfnxLVY4EMSSRp7j1k7eezutBPH7RBN/7QPnwR7hzNlEFeg==",
      "funding": [
        {
          "type": "individual",
          "url": "https://gitcoin.co/grants/13/ethersjs-complete-simple-and-tiny-2"
        },
        {
          "type": "individual",
          "url": "https://www.buymeacoffee.com/ricmoo"
        }
      ],
      "dependencies": {
        "@ethersproject/bignumber": "^5.7.0",
        "@ethersproject/constants": "^5.7.0",
        "@ethersproject/logger": "^5.7.0"
      }
    },
    "node_modules/@hapi/hoek": {
      "version": "9.3.0",
      "resolved": "https://registry.npmjs.org/@hapi/hoek/-/hoek-9.3.0.tgz",
      "integrity": "sha512-/c6rf4UJlmHlC9b5BaNvzAcFv7HZ2QHaV0D4/HNlBdvFnvQq8RI4kYdhyPCl7Xj+oWvTWQ8ujhqS53LIgAe6KQ=="
    },
    "node_modules/@hapi/topo": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/@hapi/topo/-/topo-5.1.0.tgz",
      "integrity": "sha512-foQZKJig7Ob0BMAYBfcJk8d77QtOe7Wo4ox7ff1lQYoNNAb6jwcY1ncdoy2e9wQZzvNy7ODZCYJkK8kzmcAnAg==",
      "dependencies": {
        "@hapi/hoek": "^9.0.0"
      }
    },
    "node_modules/@humanwhocodes/config-array": {
      "version": "0.13.0",
      "resolved": "https://registry.npmjs.org/@humanwhocodes/config-array/-/config-array-0.13.0.tgz",
      "integrity": "sha512-DZLEEqFWQFiyK6h5YIeynKx7JlvCYWL0cImfSRXZ9l4Sg2efkFGTuFf6vzXjK1cq6IYkU+Eg/JizXw+TD2vRNw==",
      "deprecated": "Use @eslint/config-array instead",
      "dev": true,
      "dependencies": {
        "@humanwhocodes/object-schema": "^2.0.3",
        "debug": "^4.3.1",
        "minimatch": "^3.0.5"
      },
      "engines": {
        "node": ">=10.10.0"
      }
    },
    "node_modules/@humanwhocodes/config-array/node_modules/brace-expansion": {
      "version": "1.1.11",
      "resolved": "https://registry.npmjs.org/brace-expansion/-/brace-expansion-1.1.11.tgz",
      "integrity": "sha512-iCuPHDFgrHX7H2vEI/5xpz07zSHB00TpugqhmYtVmMO6518mCuRMoOYFldEBl0g187ufozdaHgWKcYFb61qGiA==",
      "dev": true,
      "dependencies": {
        "balanced-match": "^1.0.0",
        "concat-map": "0.0.1"
      }
    },
    "node_modules/@humanwhocodes/config-array/node_modules/minimatch": {
      "version": "3.1.2",
      "resolved": "https://registry.npmjs.org/minimatch/-/minimatch-3.1.2.tgz",
      "integrity": "sha512-J7p63hRiAjw1NDEww1W7i37+ByIrOWO5XQQAzZ3VOcL0PNybwpfmV/N05zFAzwQ9USyEcX6t3UO+K5aqBQOIHw==",
      "dev": true,
      "dependencies": {
        "brace-expansion": "^1.1.7"
      },
      "engines": {
        "node": "*"
      }
    },
    "node_modules/@humanwhocodes/module-importer": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@humanwhocodes/module-importer/-/module-importer-1.0.1.tgz",
      "integrity": "sha512-bxveV4V8v5Yb4ncFTT3rPSgZBOpCkjfK0y4oVVVJwIuDVBRMDXrPyXRL988i5ap9m9bnyEEjWfm5WkBmtffLfA==",
      "dev": true,
      "engines": {
        "node": ">=12.22"
      },
      "funding": {
        "type": "github",
        "url": "https://github.com/sponsors/nzakas"
      }
    },
    "node_modules/@humanwhocodes/object-schema": {
      "version": "2.0.3",
      "resolved": "https://registry.npmjs.org/@humanwhocodes/object-schema/-/object-schema-2.0.3.tgz",
      "integrity": "sha512-93zYdMES/c1D69yZiKDBj0V24vqNzB/koF26KPaagAfd3P/4gUlh3Dys5ogAK+Exi9QyzlD8x/08Zt7wIKcDcA==",
      "deprecated": "Use @eslint/object-schema instead",
      "dev": true
    },
    "node_modules/@isaacs/cliui": {
      "version": "8.0.2",
      "resolved": "https://registry.npmjs.org/@isaacs/cliui/-/cliui-8.0.2.tgz",
      "integrity": "sha512-O8jcjabXaleOG9DQ0+ARXWZBTfnP4WNAqzuiJK7ll44AmxGKv/J2M4TPjxjY3znBCfvBXFzucm1twdyFybFqEA==",
      "dev": true,
      "dependencies": {
        "string-width": "^5.1.2",
        "string-width-cjs": "npm:string-width@^4.2.0",
        "strip-ansi": "^7.0.1",
        "strip-ansi-cjs": "npm:strip-ansi@^6.0.1",
        "wrap-ansi": "^8.1.0",
        "wrap-ansi-cjs": "npm:wrap-ansi@^7.0.0"
      },
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@isaacs/cliui/node_modules/ansi-regex": {
      "version": "6.1.0",
      "resolved": "https://registry.npmjs.org/ansi-regex/-/ansi-regex-6.1.0.tgz",
      "integrity": "sha512-7HSX4QQb4CspciLpVFwyRe79O3xsIZDDLER21kERQ71oaPodF8jL725AgJMFAYbooIqolJoRLuM81SpeUkpkvA==",
      "dev": true,
      "engines": {
        "node": ">=12"
      },
      "funding": {
        "url": "https://github.com/chalk/ansi-regex?sponsor=1"
      }
    },
    "node_modules/@isaacs/cliui/node_modules/ansi-styles": {
      "version": "6.2.1",
      "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-6.2.1.tgz",
      "integrity": "sha512-bN798gFfQX+viw3R7yrGWRqnrN2oRkEkUjjl4JNn4E8GxxbjtG3FbrEIIY3l8/hrwUwIeCZvi4QuOTP4MErVug==",
      "dev": true,
      "engines": {
        "node": ">=12"
      },
      "funding": {
        "url": "https://github.com/chalk/ansi-styles?sponsor=1"
      }
    },
    "node_modules/@isaacs/cliui/node_modules/emoji-regex": {
      "version": "9.2.2",
      "resolved": "https://registry.npmjs.org/emoji-regex/-/emoji-regex-9.2.2.tgz",
      "integrity": "sha512-L18DaJsXSUk2+42pv8mLs5jJT2hqFkFE4j21wOmgbUqsZ2hL72NsUU785g9RXgo3s0ZNgVl42TiHp3ZtOv/Vyg==",
      "dev": true
    },
    "node_modules/@isaacs/cliui/node_modules/string-width": {
      "version": "5.1.2",
      "resolved": "https://registry.npmjs.org/string-width/-/string-width-5.1.2.tgz",
      "integrity": "sha512-HnLOCR3vjcY8beoNLtcjZ5/nxn2afmME6lhrDrebokqMap+XbeW8n9TXpPDOqdGK5qcI3oT0GKTW6wC7EMiVqA==",
      "dev": true,
      "dependencies": {
        "eastasianwidth": "^0.2.0",
        "emoji-regex": "^9.2.2",
        "strip-ansi": "^7.0.1"
      },
      "engines": {
        "node": ">=12"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/@isaacs/cliui/node_modules/strip-ansi": {
      "version": "7.1.0",
      "resolved": "https://registry.npmjs.org/strip-ansi/-/strip-ansi-7.1.0.tgz",
      "integrity": "sha512-iq6eVVI64nQQTRYq2KtEg2d2uU7LElhTJwsH4YzIHZshxlgZms/wIc4VoDQTlG/IvVIrBKG06CrZnp0qv7hkcQ==",
      "dev": true,
      "dependencies": {
        "ansi-regex": "^6.0.1"
      },
      "engines": {
        "node": ">=12"
      },
      "funding": {
        "url": "https://github.com/chalk/strip-ansi?sponsor=1"
      }
    },
    "node_modules/@isaacs/cliui/node_modules/wrap-ansi": {
      "version": "8.1.0",
      "resolved": "https://registry.npmjs.org/wrap-ansi/-/wrap-ansi-8.1.0.tgz",
      "integrity": "sha512-si7QWI6zUMq56bESFvagtmzMdGOtoxfR+Sez11Mobfc7tm+VkUckk9bW2UeffTGVUbOksxmSw0AA2gs8g71NCQ==",
      "dev": true,
      "dependencies": {
        "ansi-styles": "^6.1.0",
        "string-width": "^5.0.1",
        "strip-ansi": "^7.0.1"
      },
      "engines": {
        "node": ">=12"
      },
      "funding": {
        "url": "https://github.com/chalk/wrap-ansi?sponsor=1"
      }
    },
    "node_modules/@jridgewell/gen-mapping": {
      "version": "0.3.5",
      "resolved": "https://registry.npmjs.org/@jridgewell/gen-mapping/-/gen-mapping-0.3.5.tgz",
      "integrity": "sha512-IzL8ZoEDIBRWEzlCcRhOaCupYyN5gdIK+Q6fbFdPDg6HqX6jpkItn7DFIpW9LQzXG6Df9sA7+OKnq0qlz/GaQg==",
      "dev": true,
      "dependencies": {
        "@jridgewell/set-array": "^1.2.1",
        "@jridgewell/sourcemap-codec": "^1.4.10",
        "@jridgewell/trace-mapping": "^0.3.24"
      },
      "engines": {
        "node": ">=6.0.0"
      }
    },
    "node_modules/@jridgewell/resolve-uri": {
      "version": "3.1.2",
      "resolved": "https://registry.npmjs.org/@jridgewell/resolve-uri/-/resolve-uri-3.1.2.tgz",
      "integrity": "sha512-bRISgCIjP20/tbWSPWMEi54QVPRZExkuD9lJL+UIxUKtwVJA8wW1Trb1jMs1RFXo1CBTNZ/5hpC9QvmKWdopKw==",
      "dev": true,
      "engines": {
        "node": ">=6.0.0"
      }
    },
    "node_modules/@jridgewell/set-array": {
      "version": "1.2.1",
      "resolved": "https://registry.npmjs.org/@jridgewell/set-array/-/set-array-1.2.1.tgz",
      "integrity": "sha512-R8gLRTZeyp03ymzP/6Lil/28tGeGEzhx1q2k703KGWRAI1VdvPIXdG70VJc2pAMw3NA6JKL5hhFu1sJX0Mnn/A==",
      "dev": true,
      "engines": {
        "node": ">=6.0.0"
      }
    },
    "node_modules/@jridgewell/sourcemap-codec": {
      "version": "1.5.0",
      "resolved": "https://registry.npmjs.org/@jridgewell/sourcemap-codec/-/sourcemap-codec-1.5.0.tgz",
      "integrity": "sha512-gv3ZRaISU3fjPAgNsriBRqGWQL6quFx04YMPW/zD8XMLsU32mhCCbfbO6KZFLjvYpCZ8zyDEgqsgf+PwPaM7GQ==",
      "dev": true
    },
    "node_modules/@jridgewell/trace-mapping": {
      "version": "0.3.25",
      "resolved": "https://registry.npmjs.org/@jridgewell/trace-mapping/-/trace-mapping-0.3.25.tgz",
      "integrity": "sha512-vNk6aEwybGtawWmy/PzwnGDOjCkLWSD2wqvjGGAgOAwCGWySYXfYoxt00IJkTF+8Lb57DwOb3Aa0o9CApepiYQ==",
      "dev": true,
      "dependencies": {
        "@jridgewell/resolve-uri": "^3.1.0",
        "@jridgewell/sourcemap-codec": "^1.4.14"
      }
    },
    "node_modules/@lit-labs/ssr-dom-shim": {
      "version": "1.2.1",
      "resolved": "https://registry.npmjs.org/@lit-labs/ssr-dom-shim/-/ssr-dom-shim-1.2.1.tgz",
      "integrity": "sha512-wx4aBmgeGvFmOKucFKY+8VFJSYZxs9poN3SDNQFF6lT6NrQUnHiPB2PWz2sc4ieEcAaYYzN+1uWahEeTq2aRIQ=="
    },
    "node_modules/@lit/reactive-element": {
      "version": "1.6.3",
      "resolved": "https://registry.npmjs.org/@lit/reactive-element/-/reactive-element-1.6.3.tgz",
      "integrity": "sha512-QuTgnG52Poic7uM1AN5yJ09QMe0O28e10XzSvWDz02TJiiKee4stsiownEIadWm8nYzyDAyT+gKzUoZmiWQtsQ==",
      "dependencies": {
        "@lit-labs/ssr-dom-shim": "^1.0.0"
      }
    },
    "node_modules/@metamask/abi-utils": {
      "version": "2.0.4",
      "resolved": "https://registry.npmjs.org/@metamask/abi-utils/-/abi-utils-2.0.4.tgz",
      "integrity": "sha512-StnIgUB75x7a7AgUhiaUZDpCsqGp7VkNnZh2XivXkJ6mPkE83U8ARGQj5MbRis7VJY8BC5V1AbB1fjdh0hupPQ==",
      "dependencies": {
        "@metamask/superstruct": "^3.1.0",
        "@metamask/utils": "^9.0.0"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@metamask/abi-utils/node_modules/@metamask/utils": {
      "version": "9.3.0",
      "resolved": "https://registry.npmjs.org/@metamask/utils/-/utils-9.3.0.tgz",
      "integrity": "sha512-w8CVbdkDrVXFJbfBSlDfafDR6BAkpDmv1bC1UJVCoVny5tW2RKAdn9i68Xf7asYT4TnUhl/hN4zfUiKQq9II4g==",
      "dependencies": {
        "@ethereumjs/tx": "^4.2.0",
        "@metamask/superstruct": "^3.1.0",
        "@noble/hashes": "^1.3.1",
        "@scure/base": "^1.1.3",
        "@types/debug": "^4.1.7",
        "debug": "^4.3.4",
        "pony-cause": "^2.1.10",
        "semver": "^7.5.4",
        "uuid": "^9.0.1"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@metamask/abi-utils/node_modules/uuid": {
      "version": "9.0.1",
      "resolved": "https://registry.npmjs.org/uuid/-/uuid-9.0.1.tgz",
      "integrity": "sha512-b+1eJOlsR9K8HJpow9Ok3fiWOWSIcIzXodvv0rQjVoOVNpWMpxf1wZNpt4y9h10odCNrqnYp1OBzRktckBe3sA==",
      "funding": [
        "https://github.com/sponsors/broofa",
        "https://github.com/sponsors/ctavan"
      ],
      "bin": {
        "uuid": "dist/bin/uuid"
      }
    },
    "node_modules/@metamask/eth-json-rpc-provider": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@metamask/eth-json-rpc-provider/-/eth-json-rpc-provider-1.0.1.tgz",
      "integrity": "sha512-whiUMPlAOrVGmX8aKYVPvlKyG4CpQXiNNyt74vE1xb5sPvmx5oA7B/kOi/JdBvhGQq97U1/AVdXEdk2zkP8qyA==",
      "dependencies": {
        "@metamask/json-rpc-engine": "^7.0.0",
        "@metamask/safe-event-emitter": "^3.0.0",
        "@metamask/utils": "^5.0.1"
      },
      "engines": {
        "node": ">=14.0.0"
      }
    },
    "node_modules/@metamask/eth-sig-util": {
      "version": "7.0.3",
      "resolved": "https://registry.npmjs.org/@metamask/eth-sig-util/-/eth-sig-util-7.0.3.tgz",
      "integrity": "sha512-PAtGnOkYvh90k2lEZldq/FK7GTLF6WxE+2bV85PoA3pqlJnmJCAY62tuvxHSwnVngSKlc4mcNvjnUg2eYO6JGg==",
      "dependencies": {
        "@ethereumjs/util": "^8.1.0",
        "@metamask/abi-utils": "^2.0.4",
        "@metamask/utils": "^9.0.0",
        "@scure/base": "~1.1.3",
        "ethereum-cryptography": "^2.1.2",
        "tweetnacl": "^1.0.3"
      },
      "engines": {
        "node": "^16.20 || ^18.16 || >=20"
      }
    },
    "node_modules/@metamask/eth-sig-util/node_modules/@metamask/utils": {
      "version": "9.3.0",
      "resolved": "https://registry.npmjs.org/@metamask/utils/-/utils-9.3.0.tgz",
      "integrity": "sha512-w8CVbdkDrVXFJbfBSlDfafDR6BAkpDmv1bC1UJVCoVny5tW2RKAdn9i68Xf7asYT4TnUhl/hN4zfUiKQq9II4g==",
      "dependencies": {
        "@ethereumjs/tx": "^4.2.0",
        "@metamask/superstruct": "^3.1.0",
        "@noble/hashes": "^1.3.1",
        "@scure/base": "^1.1.3",
        "@types/debug": "^4.1.7",
        "debug": "^4.3.4",
        "pony-cause": "^2.1.10",
        "semver": "^7.5.4",
        "uuid": "^9.0.1"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@metamask/eth-sig-util/node_modules/uuid": {
      "version": "9.0.1",
      "resolved": "https://registry.npmjs.org/uuid/-/uuid-9.0.1.tgz",
      "integrity": "sha512-b+1eJOlsR9K8HJpow9Ok3fiWOWSIcIzXodvv0rQjVoOVNpWMpxf1wZNpt4y9h10odCNrqnYp1OBzRktckBe3sA==",
      "funding": [
        "https://github.com/sponsors/broofa",
        "https://github.com/sponsors/ctavan"
      ],
      "bin": {
        "uuid": "dist/bin/uuid"
      }
    },
    "node_modules/@metamask/json-rpc-engine": {
      "version": "7.3.3",
      "resolved": "https://registry.npmjs.org/@metamask/json-rpc-engine/-/json-rpc-engine-7.3.3.tgz",
      "integrity": "sha512-dwZPq8wx9yV3IX2caLi9q9xZBw2XeIoYqdyihDDDpuHVCEiqadJLwqM3zy+uwf6F1QYQ65A8aOMQg1Uw7LMLNg==",
      "dependencies": {
        "@metamask/rpc-errors": "^6.2.1",
        "@metamask/safe-event-emitter": "^3.0.0",
        "@metamask/utils": "^8.3.0"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@metamask/json-rpc-engine/node_modules/@metamask/utils": {
      "version": "8.5.0",
      "resolved": "https://registry.npmjs.org/@metamask/utils/-/utils-8.5.0.tgz",
      "integrity": "sha512-I6bkduevXb72TIM9q2LRO63JSsF9EXduh3sBr9oybNX2hNNpr/j1tEjXrsG0Uabm4MJ1xkGAQEMwifvKZIkyxQ==",
      "dependencies": {
        "@ethereumjs/tx": "^4.2.0",
        "@metamask/superstruct": "^3.0.0",
        "@noble/hashes": "^1.3.1",
        "@scure/base": "^1.1.3",
        "@types/debug": "^4.1.7",
        "debug": "^4.3.4",
        "pony-cause": "^2.1.10",
        "semver": "^7.5.4",
        "uuid": "^9.0.1"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@metamask/json-rpc-engine/node_modules/uuid": {
      "version": "9.0.1",
      "resolved": "https://registry.npmjs.org/uuid/-/uuid-9.0.1.tgz",
      "integrity": "sha512-b+1eJOlsR9K8HJpow9Ok3fiWOWSIcIzXodvv0rQjVoOVNpWMpxf1wZNpt4y9h10odCNrqnYp1OBzRktckBe3sA==",
      "funding": [
        "https://github.com/sponsors/broofa",
        "https://github.com/sponsors/ctavan"
      ],
      "bin": {
        "uuid": "dist/bin/uuid"
      }
    },
    "node_modules/@metamask/rpc-errors": {
      "version": "6.4.0",
      "resolved": "https://registry.npmjs.org/@metamask/rpc-errors/-/rpc-errors-6.4.0.tgz",
      "integrity": "sha512-1ugFO1UoirU2esS3juZanS/Fo8C8XYocCuBpfZI5N7ECtoG+zu0wF+uWZASik6CkO6w9n/Iebt4iI4pT0vptpg==",
      "dependencies": {
        "@metamask/utils": "^9.0.0",
        "fast-safe-stringify": "^2.0.6"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@metamask/rpc-errors/node_modules/@metamask/utils": {
      "version": "9.3.0",
      "resolved": "https://registry.npmjs.org/@metamask/utils/-/utils-9.3.0.tgz",
      "integrity": "sha512-w8CVbdkDrVXFJbfBSlDfafDR6BAkpDmv1bC1UJVCoVny5tW2RKAdn9i68Xf7asYT4TnUhl/hN4zfUiKQq9II4g==",
      "dependencies": {
        "@ethereumjs/tx": "^4.2.0",
        "@metamask/superstruct": "^3.1.0",
        "@noble/hashes": "^1.3.1",
        "@scure/base": "^1.1.3",
        "@types/debug": "^4.1.7",
        "debug": "^4.3.4",
        "pony-cause": "^2.1.10",
        "semver": "^7.5.4",
        "uuid": "^9.0.1"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@metamask/rpc-errors/node_modules/uuid": {
      "version": "9.0.1",
      "resolved": "https://registry.npmjs.org/uuid/-/uuid-9.0.1.tgz",
      "integrity": "sha512-b+1eJOlsR9K8HJpow9Ok3fiWOWSIcIzXodvv0rQjVoOVNpWMpxf1wZNpt4y9h10odCNrqnYp1OBzRktckBe3sA==",
      "funding": [
        "https://github.com/sponsors/broofa",
        "https://github.com/sponsors/ctavan"
      ],
      "bin": {
        "uuid": "dist/bin/uuid"
      }
    },
    "node_modules/@metamask/safe-event-emitter": {
      "version": "3.1.2",
      "resolved": "https://registry.npmjs.org/@metamask/safe-event-emitter/-/safe-event-emitter-3.1.2.tgz",
      "integrity": "sha512-5yb2gMI1BDm0JybZezeoX/3XhPDOtTbcFvpTXM9kxsoZjPZFh4XciqRbpD6N86HYZqWDhEaKUDuOyR0sQHEjMA==",
      "engines": {
        "node": ">=12.0.0"
      }
    },
    "node_modules/@metamask/superstruct": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/@metamask/superstruct/-/superstruct-3.1.0.tgz",
      "integrity": "sha512-N08M56HdOgBfRKkrgCMZvQppkZGcArEop3kixNEtVbJKm6P9Cfg0YkI6X0s1g78sNrj2fWUwvJADdZuzJgFttA==",
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@metamask/utils": {
      "version": "5.0.2",
      "resolved": "https://registry.npmjs.org/@metamask/utils/-/utils-5.0.2.tgz",
      "integrity": "sha512-yfmE79bRQtnMzarnKfX7AEJBwFTxvTyw3nBQlu/5rmGXrjAeAMltoGxO62TFurxrQAFMNa/fEjIHNvungZp0+g==",
      "dependencies": {
        "@ethereumjs/tx": "^4.1.2",
        "@types/debug": "^4.1.7",
        "debug": "^4.3.4",
        "semver": "^7.3.8",
        "superstruct": "^1.0.3"
      },
      "engines": {
        "node": ">=14.0.0"
      }
    },
    "node_modules/@metamask/utils/node_modules/superstruct": {
      "version": "1.0.4",
      "resolved": "https://registry.npmjs.org/superstruct/-/superstruct-1.0.4.tgz",
      "integrity": "sha512-7JpaAoX2NGyoFlI9NBh66BQXGONc+uE+MRS5i2iOBKuS4e+ccgMDjATgZldkah+33DakBxDHiss9kvUcGAO8UQ==",
      "engines": {
        "node": ">=14.0.0"
      }
    },
    "node_modules/@motionone/animation": {
      "version": "10.18.0",
      "resolved": "https://registry.npmjs.org/@motionone/animation/-/animation-10.18.0.tgz",
      "integrity": "sha512-9z2p5GFGCm0gBsZbi8rVMOAJCtw1WqBTIPw3ozk06gDvZInBPIsQcHgYogEJ4yuHJ+akuW8g1SEIOpTOvYs8hw==",
      "dependencies": {
        "@motionone/easing": "^10.18.0",
        "@motionone/types": "^10.17.1",
        "@motionone/utils": "^10.18.0",
        "tslib": "^2.3.1"
      }
    },
    "node_modules/@motionone/animation/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@motionone/dom": {
      "version": "10.18.0",
      "resolved": "https://registry.npmjs.org/@motionone/dom/-/dom-10.18.0.tgz",
      "integrity": "sha512-bKLP7E0eyO4B2UaHBBN55tnppwRnaE3KFfh3Ps9HhnAkar3Cb69kUCJY9as8LrccVYKgHA+JY5dOQqJLOPhF5A==",
      "dependencies": {
        "@motionone/animation": "^10.18.0",
        "@motionone/generators": "^10.18.0",
        "@motionone/types": "^10.17.1",
        "@motionone/utils": "^10.18.0",
        "hey-listen": "^1.0.8",
        "tslib": "^2.3.1"
      }
    },
    "node_modules/@motionone/dom/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@motionone/easing": {
      "version": "10.18.0",
      "resolved": "https://registry.npmjs.org/@motionone/easing/-/easing-10.18.0.tgz",
      "integrity": "sha512-VcjByo7XpdLS4o9T8t99JtgxkdMcNWD3yHU/n6CLEz3bkmKDRZyYQ/wmSf6daum8ZXqfUAgFeCZSpJZIMxaCzg==",
      "dependencies": {
        "@motionone/utils": "^10.18.0",
        "tslib": "^2.3.1"
      }
    },
    "node_modules/@motionone/easing/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@motionone/generators": {
      "version": "10.18.0",
      "resolved": "https://registry.npmjs.org/@motionone/generators/-/generators-10.18.0.tgz",
      "integrity": "sha512-+qfkC2DtkDj4tHPu+AFKVfR/C30O1vYdvsGYaR13W/1cczPrrcjdvYCj0VLFuRMN+lP1xvpNZHCRNM4fBzn1jg==",
      "dependencies": {
        "@motionone/types": "^10.17.1",
        "@motionone/utils": "^10.18.0",
        "tslib": "^2.3.1"
      }
    },
    "node_modules/@motionone/generators/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@motionone/svelte": {
      "version": "10.16.4",
      "resolved": "https://registry.npmjs.org/@motionone/svelte/-/svelte-10.16.4.tgz",
      "integrity": "sha512-zRVqk20lD1xqe+yEDZhMYgftsuHc25+9JSo+r0a0OWUJFocjSV9D/+UGhX4xgJsuwB9acPzXLr20w40VnY2PQA==",
      "dependencies": {
        "@motionone/dom": "^10.16.4",
        "tslib": "^2.3.1"
      }
    },
    "node_modules/@motionone/svelte/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@motionone/types": {
      "version": "10.17.1",
      "resolved": "https://registry.npmjs.org/@motionone/types/-/types-10.17.1.tgz",
      "integrity": "sha512-KaC4kgiODDz8hswCrS0btrVrzyU2CSQKO7Ps90ibBVSQmjkrt2teqta6/sOG59v7+dPnKMAg13jyqtMKV2yJ7A=="
    },
    "node_modules/@motionone/utils": {
      "version": "10.18.0",
      "resolved": "https://registry.npmjs.org/@motionone/utils/-/utils-10.18.0.tgz",
      "integrity": "sha512-3XVF7sgyTSI2KWvTf6uLlBJ5iAgRgmvp3bpuOiQJvInd4nZ19ET8lX5unn30SlmRH7hXbBbH+Gxd0m0klJ3Xtw==",
      "dependencies": {
        "@motionone/types": "^10.17.1",
        "hey-listen": "^1.0.8",
        "tslib": "^2.3.1"
      }
    },
    "node_modules/@motionone/utils/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@motionone/vue": {
      "version": "10.16.4",
      "resolved": "https://registry.npmjs.org/@motionone/vue/-/vue-10.16.4.tgz",
      "integrity": "sha512-z10PF9JV6SbjFq+/rYabM+8CVlMokgl8RFGvieSGNTmrkQanfHn+15XBrhG3BgUfvmTeSeyShfOHpG0i9zEdcg==",
      "deprecated": "Motion One for Vue is deprecated. Use Oku Motion instead https://oku-ui.com/motion",
      "dependencies": {
        "@motionone/dom": "^10.16.4",
        "tslib": "^2.3.1"
      }
    },
    "node_modules/@motionone/vue/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@noble/curves": {
      "version": "1.6.0",
      "resolved": "https://registry.npmjs.org/@noble/curves/-/curves-1.6.0.tgz",
      "integrity": "sha512-TlaHRXDehJuRNR9TfZDNQ45mMEd5dwUwmicsafcIX4SsNiqnCHKjE/1alYPd/lDRVhxdhUAlv8uEhMCI5zjIJQ==",
      "dependencies": {
        "@noble/hashes": "1.5.0"
      },
      "engines": {
        "node": "^14.21.3 || >=16"
      },
      "funding": {
        "url": "https://paulmillr.com/funding/"
      }
    },
    "node_modules/@noble/hashes": {
      "version": "1.5.0",
      "resolved": "https://registry.npmjs.org/@noble/hashes/-/hashes-1.5.0.tgz",
      "integrity": "sha512-1j6kQFb7QRru7eKN3ZDvRcP13rugwdxZqCjbiAVZfIJwgj2A65UmT4TgARXGlXgnRkORLTDTrO19ZErt7+QXgA==",
      "engines": {
        "node": "^14.21.3 || >=16"
      },
      "funding": {
        "url": "https://paulmillr.com/funding/"
      }
    },
    "node_modules/@nodelib/fs.scandir": {
      "version": "2.1.5",
      "resolved": "https://registry.npmjs.org/@nodelib/fs.scandir/-/fs.scandir-2.1.5.tgz",
      "integrity": "sha512-vq24Bq3ym5HEQm2NKCr3yXDwjc7vTsEThRDnkp2DK9p1uqLR+DHurm/NOTo0KG7HYHU7eppKZj3MyqYuMBf62g==",
      "dev": true,
      "dependencies": {
        "@nodelib/fs.stat": "2.0.5",
        "run-parallel": "^1.1.9"
      },
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/@nodelib/fs.stat": {
      "version": "2.0.5",
      "resolved": "https://registry.npmjs.org/@nodelib/fs.stat/-/fs.stat-2.0.5.tgz",
      "integrity": "sha512-RkhPPp2zrqDAQA/2jNhnztcPAlv64XdhIp7a7454A5ovI7Bukxgt7MX7udwAu3zg1DcpPU0rz3VV1SeaqvY4+A==",
      "dev": true,
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/@nodelib/fs.walk": {
      "version": "1.2.8",
      "resolved": "https://registry.npmjs.org/@nodelib/fs.walk/-/fs.walk-1.2.8.tgz",
      "integrity": "sha512-oGB+UxlgWcgQkgwo8GcEGwemoTFt3FIO9ababBmaGwXIoBKZ+GTy0pP185beGg7Llih/NSHSV2XAs1lnznocSg==",
      "dev": true,
      "dependencies": {
        "@nodelib/fs.scandir": "2.1.5",
        "fastq": "^1.6.0"
      },
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/@parcel/watcher": {
      "version": "2.4.1",
      "resolved": "https://registry.npmjs.org/@parcel/watcher/-/watcher-2.4.1.tgz",
      "integrity": "sha512-HNjmfLQEVRZmHRET336f20H/8kOozUGwk7yajvsonjNxbj2wBTK1WsQuHkD5yYh9RxFGL2EyDHryOihOwUoKDA==",
      "dependencies": {
        "detect-libc": "^1.0.3",
        "is-glob": "^4.0.3",
        "micromatch": "^4.0.5",
        "node-addon-api": "^7.0.0"
      },
      "engines": {
        "node": ">= 10.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/parcel"
      },
      "optionalDependencies": {
        "@parcel/watcher-android-arm64": "2.4.1",
        "@parcel/watcher-darwin-arm64": "2.4.1",
        "@parcel/watcher-darwin-x64": "2.4.1",
        "@parcel/watcher-freebsd-x64": "2.4.1",
        "@parcel/watcher-linux-arm-glibc": "2.4.1",
        "@parcel/watcher-linux-arm64-glibc": "2.4.1",
        "@parcel/watcher-linux-arm64-musl": "2.4.1",
        "@parcel/watcher-linux-x64-glibc": "2.4.1",
        "@parcel/watcher-linux-x64-musl": "2.4.1",
        "@parcel/watcher-win32-arm64": "2.4.1",
        "@parcel/watcher-win32-ia32": "2.4.1",
        "@parcel/watcher-win32-x64": "2.4.1"
      }
    },
    "node_modules/@parcel/watcher-android-arm64": {
      "version": "2.4.1",
      "resolved": "https://registry.npmjs.org/@parcel/watcher-android-arm64/-/watcher-android-arm64-2.4.1.tgz",
      "integrity": "sha512-LOi/WTbbh3aTn2RYddrO8pnapixAziFl6SMxHM69r3tvdSm94JtCenaKgk1GRg5FJ5wpMCpHeW+7yqPlvZv7kg==",
      "cpu": [
        "arm64"
      ],
      "optional": true,
      "os": [
        "android"
      ],
      "engines": {
        "node": ">= 10.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/parcel"
      }
    },
    "node_modules/@parcel/watcher-darwin-arm64": {
      "version": "2.4.1",
      "resolved": "https://registry.npmjs.org/@parcel/watcher-darwin-arm64/-/watcher-darwin-arm64-2.4.1.tgz",
      "integrity": "sha512-ln41eihm5YXIY043vBrrHfn94SIBlqOWmoROhsMVTSXGh0QahKGy77tfEywQ7v3NywyxBBkGIfrWRHm0hsKtzA==",
      "cpu": [
        "arm64"
      ],
      "optional": true,
      "os": [
        "darwin"
      ],
      "engines": {
        "node": ">= 10.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/parcel"
      }
    },
    "node_modules/@parcel/watcher-darwin-x64": {
      "version": "2.4.1",
      "resolved": "https://registry.npmjs.org/@parcel/watcher-darwin-x64/-/watcher-darwin-x64-2.4.1.tgz",
      "integrity": "sha512-yrw81BRLjjtHyDu7J61oPuSoeYWR3lDElcPGJyOvIXmor6DEo7/G2u1o7I38cwlcoBHQFULqF6nesIX3tsEXMg==",
      "cpu": [
        "x64"
      ],
      "optional": true,
      "os": [
        "darwin"
      ],
      "engines": {
        "node": ">= 10.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/parcel"
      }
    },
    "node_modules/@parcel/watcher-freebsd-x64": {
      "version": "2.4.1",
      "resolved": "https://registry.npmjs.org/@parcel/watcher-freebsd-x64/-/watcher-freebsd-x64-2.4.1.tgz",
      "integrity": "sha512-TJa3Pex/gX3CWIx/Co8k+ykNdDCLx+TuZj3f3h7eOjgpdKM+Mnix37RYsYU4LHhiYJz3DK5nFCCra81p6g050w==",
      "cpu": [
        "x64"
      ],
      "optional": true,
      "os": [
        "freebsd"
      ],
      "engines": {
        "node": ">= 10.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/parcel"
      }
    },
    "node_modules/@parcel/watcher-linux-arm-glibc": {
      "version": "2.4.1",
      "resolved": "https://registry.npmjs.org/@parcel/watcher-linux-arm-glibc/-/watcher-linux-arm-glibc-2.4.1.tgz",
      "integrity": "sha512-4rVYDlsMEYfa537BRXxJ5UF4ddNwnr2/1O4MHM5PjI9cvV2qymvhwZSFgXqbS8YoTk5i/JR0L0JDs69BUn45YA==",
      "cpu": [
        "arm"
      ],
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">= 10.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/parcel"
      }
    },
    "node_modules/@parcel/watcher-linux-arm64-glibc": {
      "version": "2.4.1",
      "resolved": "https://registry.npmjs.org/@parcel/watcher-linux-arm64-glibc/-/watcher-linux-arm64-glibc-2.4.1.tgz",
      "integrity": "sha512-BJ7mH985OADVLpbrzCLgrJ3TOpiZggE9FMblfO65PlOCdG++xJpKUJ0Aol74ZUIYfb8WsRlUdgrZxKkz3zXWYA==",
      "cpu": [
        "arm64"
      ],
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">= 10.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/parcel"
      }
    },
    "node_modules/@parcel/watcher-linux-arm64-musl": {
      "version": "2.4.1",
      "resolved": "https://registry.npmjs.org/@parcel/watcher-linux-arm64-musl/-/watcher-linux-arm64-musl-2.4.1.tgz",
      "integrity": "sha512-p4Xb7JGq3MLgAfYhslU2SjoV9G0kI0Xry0kuxeG/41UfpjHGOhv7UoUDAz/jb1u2elbhazy4rRBL8PegPJFBhA==",
      "cpu": [
        "arm64"
      ],
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">= 10.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/parcel"
      }
    },
    "node_modules/@parcel/watcher-linux-x64-glibc": {
      "version": "2.4.1",
      "resolved": "https://registry.npmjs.org/@parcel/watcher-linux-x64-glibc/-/watcher-linux-x64-glibc-2.4.1.tgz",
      "integrity": "sha512-s9O3fByZ/2pyYDPoLM6zt92yu6P4E39a03zvO0qCHOTjxmt3GHRMLuRZEWhWLASTMSrrnVNWdVI/+pUElJBBBg==",
      "cpu": [
        "x64"
      ],
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">= 10.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/parcel"
      }
    },
    "node_modules/@parcel/watcher-linux-x64-musl": {
      "version": "2.4.1",
      "resolved": "https://registry.npmjs.org/@parcel/watcher-linux-x64-musl/-/watcher-linux-x64-musl-2.4.1.tgz",
      "integrity": "sha512-L2nZTYR1myLNST0O632g0Dx9LyMNHrn6TOt76sYxWLdff3cB22/GZX2UPtJnaqQPdCRoszoY5rcOj4oMTtp5fQ==",
      "cpu": [
        "x64"
      ],
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">= 10.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/parcel"
      }
    },
    "node_modules/@parcel/watcher-wasm": {
      "version": "2.4.1",
      "resolved": "https://registry.npmjs.org/@parcel/watcher-wasm/-/watcher-wasm-2.4.1.tgz",
      "integrity": "sha512-/ZR0RxqxU/xxDGzbzosMjh4W6NdYFMqq2nvo2b8SLi7rsl/4jkL8S5stIikorNkdR50oVDvqb/3JT05WM+CRRA==",
      "bundleDependencies": [
        "napi-wasm"
      ],
      "dependencies": {
        "is-glob": "^4.0.3",
        "micromatch": "^4.0.5",
        "napi-wasm": "^1.1.0"
      },
      "engines": {
        "node": ">= 10.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/parcel"
      }
    },
    "node_modules/@parcel/watcher-wasm/node_modules/napi-wasm": {
      "version": "1.1.0",
      "inBundle": true,
      "license": "MIT"
    },
    "node_modules/@parcel/watcher-win32-arm64": {
      "version": "2.4.1",
      "resolved": "https://registry.npmjs.org/@parcel/watcher-win32-arm64/-/watcher-win32-arm64-2.4.1.tgz",
      "integrity": "sha512-Uq2BPp5GWhrq/lcuItCHoqxjULU1QYEcyjSO5jqqOK8RNFDBQnenMMx4gAl3v8GiWa59E9+uDM7yZ6LxwUIfRg==",
      "cpu": [
        "arm64"
      ],
      "optional": true,
      "os": [
        "win32"
      ],
      "engines": {
        "node": ">= 10.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/parcel"
      }
    },
    "node_modules/@parcel/watcher-win32-ia32": {
      "version": "2.4.1",
      "resolved": "https://registry.npmjs.org/@parcel/watcher-win32-ia32/-/watcher-win32-ia32-2.4.1.tgz",
      "integrity": "sha512-maNRit5QQV2kgHFSYwftmPBxiuK5u4DXjbXx7q6eKjq5dsLXZ4FJiVvlcw35QXzk0KrUecJmuVFbj4uV9oYrcw==",
      "cpu": [
        "ia32"
      ],
      "optional": true,
      "os": [
        "win32"
      ],
      "engines": {
        "node": ">= 10.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/parcel"
      }
    },
    "node_modules/@parcel/watcher-win32-x64": {
      "version": "2.4.1",
      "resolved": "https://registry.npmjs.org/@parcel/watcher-win32-x64/-/watcher-win32-x64-2.4.1.tgz",
      "integrity": "sha512-+DvS92F9ezicfswqrvIRM2njcYJbd5mb9CUgtrHCHmvn7pPPa+nMDRu1o1bYYz/l5IB2NVGNJWiH7h1E58IF2A==",
      "cpu": [
        "x64"
      ],
      "optional": true,
      "os": [
        "win32"
      ],
      "engines": {
        "node": ">= 10.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/parcel"
      }
    },
    "node_modules/@parcel/watcher/node_modules/node-addon-api": {
      "version": "7.1.1",
      "resolved": "https://registry.npmjs.org/node-addon-api/-/node-addon-api-7.1.1.tgz",
      "integrity": "sha512-5m3bsyrjFWE1xf7nz7YXdN4udnVtXK6/Yfgn5qnahL6bCkf2yKt4k3nuTKAtT4r3IG8JNR2ncsIMdZuAzJjHQQ=="
    },
    "node_modules/@particle-network/analytics": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@particle-network/analytics/-/analytics-1.0.1.tgz",
      "integrity": "sha512-ApcSMo1BXQlywO+lvOpG3Y2/SVGNCpJzXO/4e3zHzE/9j+uMehsilDzPwWQwLhrCXZYwVm7mmE71Gs36yobiNw==",
      "dependencies": {
        "hash.js": "^1.1.7",
        "uuidv4": "^6.2.13"
      }
    },
    "node_modules/@particle-network/auth-core": {
      "version": "1.5.2",
      "resolved": "https://registry.npmjs.org/@particle-network/auth-core/-/auth-core-1.5.2.tgz",
      "integrity": "sha512-fdGkuhlZ+wMzoSthA3scKxv3qLAwVMaHgxa8pKZNA7O6WwevHnWRY7VrZYHORPzxtpnn9RyYf8h5Cls4+u2bcA==",
      "dependencies": {
        "@aws-sdk/client-cognito-identity": "^3.58.0",
        "@aws-sdk/client-kms": "^3.58.0",
        "@aws-sdk/credential-providers": "^3.58.0",
        "@ethereumjs/tx": "^4.2.0",
        "@ethereumjs/util": "^8.1.0",
        "@ethersproject/bignumber": "^5.7.0",
        "@ethersproject/units": "^5.7.0",
        "@metamask/eth-sig-util": "^7.0.0",
        "@metamask/rpc-errors": "^6.0.0",
        "@particle-network/analytics": "^1.0.1",
        "@particle-network/chains": ">=1.3.8",
        "@particle-network/thresh-sig": "^0.7.8",
        "@solana/web3.js": "^1.73.0",
        "axios": "^1.5.0",
        "base64url": "^3.0.1",
        "bs58": "^5.0.0",
        "crypto-js": "^4.1.1",
        "fast-json-stable-stringify": "^2.1.0",
        "lzutf8": "^0.6.3",
        "uuid": "^9.0.1"
      },
      "engines": {
        "node": ">=16"
      }
    },
    "node_modules/@particle-network/auth-core-modal": {
      "version": "1.5.2",
      "resolved": "https://registry.npmjs.org/@particle-network/auth-core-modal/-/auth-core-modal-1.5.2.tgz",
      "integrity": "sha512-dZUig6zfC/DVS7MBfXIm3By4Bh+xz3OLkKi9CxiMkAem7ePx2Nse57B/hS6cViwoDH1VksbxYeGBdCZiljFsJg==",
      "dependencies": {
        "@particle-network/analytics": "^1.0.1",
        "@particle-network/auth-core": "^1.5.2",
        "@particle-network/wallet": "^1.4.6",
        "@solana/spl-token": "^0.2.0",
        "ahooks": "^3.7.8",
        "antd": "^4",
        "bn.js": "^5.2.1",
        "country-flag-icons": "^1.4.26",
        "dayjs": "^1.11.7",
        "ethjs-unit": "^0.1.6",
        "i18next": "^23.2.3",
        "json-toy": "^2.0.2",
        "libphonenumber-js": "^1.10.36",
        "lodash": "^4.17.21",
        "lottie-react": "^2.4.0",
        "lzutf8": "^0.6.2",
        "numbro": "^2.3.6",
        "qs": "^6.10.3",
        "react-copy-to-clipboard": "^5.1.0",
        "react-i18next": "^13.3.0",
        "react-shadow": "^20.4.0",
        "uuid": "^8.3.2"
      },
      "engines": {
        "node": ">=16"
      },
      "peerDependencies": {
        "react": ">=17.0.0"
      }
    },
    "node_modules/@particle-network/auth-core-modal/node_modules/i18next": {
      "version": "23.16.4",
      "resolved": "https://registry.npmjs.org/i18next/-/i18next-23.16.4.tgz",
      "integrity": "sha512-9NIYBVy9cs4wIqzurf7nLXPyf3R78xYbxExVqHLK9od3038rjpyOEzW+XB130kZ1N4PZ9inTtJ471CRJ4Ituyg==",
      "funding": [
        {
          "type": "individual",
          "url": "https://locize.com"
        },
        {
          "type": "individual",
          "url": "https://locize.com/i18next.html"
        },
        {
          "type": "individual",
          "url": "https://www.i18next.com/how-to/faq#i18next-is-awesome.-how-can-i-support-the-project"
        }
      ],
      "dependencies": {
        "@babel/runtime": "^7.23.2"
      }
    },
    "node_modules/@particle-network/auth-core-modal/node_modules/react-i18next": {
      "version": "13.5.0",
      "resolved": "https://registry.npmjs.org/react-i18next/-/react-i18next-13.5.0.tgz",
      "integrity": "sha512-CFJ5NDGJ2MUyBohEHxljOq/39NQ972rh1ajnadG9BjTk+UXbHLq4z5DKEbEQBDoIhUmmbuS/fIMJKo6VOax1HA==",
      "dependencies": {
        "@babel/runtime": "^7.22.5",
        "html-parse-stringify": "^3.0.1"
      },
      "peerDependencies": {
        "i18next": ">= 23.2.3",
        "react": ">= 16.8.0"
      },
      "peerDependenciesMeta": {
        "react-dom": {
          "optional": true
        },
        "react-native": {
          "optional": true
        }
      }
    },
    "node_modules/@particle-network/auth-core/node_modules/base-x": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/base-x/-/base-x-4.0.0.tgz",
      "integrity": "sha512-FuwxlW4H5kh37X/oW59pwTzzTKRzfrrQwhmyspRM7swOEZcHtDZSCt45U6oKgtuFE+WYPblePMVIPR4RZrh/hw=="
    },
    "node_modules/@particle-network/auth-core/node_modules/bs58": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/bs58/-/bs58-5.0.0.tgz",
      "integrity": "sha512-r+ihvQJvahgYT50JD05dyJNKlmmSlMoOGwn1lCcEzanPglg7TxYjioQUYehQ9mAR/+hOSd2jRc/Z2y5UxBymvQ==",
      "dependencies": {
        "base-x": "^4.0.0"
      }
    },
    "node_modules/@particle-network/auth-core/node_modules/uuid": {
      "version": "9.0.1",
      "resolved": "https://registry.npmjs.org/uuid/-/uuid-9.0.1.tgz",
      "integrity": "sha512-b+1eJOlsR9K8HJpow9Ok3fiWOWSIcIzXodvv0rQjVoOVNpWMpxf1wZNpt4y9h10odCNrqnYp1OBzRktckBe3sA==",
      "funding": [
        "https://github.com/sponsors/broofa",
        "https://github.com/sponsors/ctavan"
      ],
      "bin": {
        "uuid": "dist/bin/uuid"
      }
    },
    "node_modules/@particle-network/chains": {
      "version": "1.7.6",
      "resolved": "https://registry.npmjs.org/@particle-network/chains/-/chains-1.7.6.tgz",
      "integrity": "sha512-M36pzJO3SO5l8b75Hap6Jd0Ju0gzpIKTlTOrU5CIXWZZzLjyRAy7wqk8JlCJ9okMCB6asy8cFeX5Ts9S8p+OCg=="
    },
    "node_modules/@particle-network/connectkit": {
      "version": "1.4.8",
      "resolved": "https://registry.npmjs.org/@particle-network/connectkit/-/connectkit-1.4.8.tgz",
      "integrity": "sha512-Od4r2OVfagCjfycCJIUbLyn6C/TiUk8H8MCAIrCjNgufT91r8sqBiFwObbkKDYwzq8g8HYOpJKTymw6Q14dCSg==",
      "dependencies": {
        "@particle-network/auth-core-modal": "^1.5.1",
        "@particle-network/connectors": "^1.4.5",
        "i18next": "^22.0.6",
        "qrcode": "^1.5.1",
        "react-i18next": "^12.0.0",
        "react-svg": "^16.1.6"
      }
    },
    "node_modules/@particle-network/connectors": {
      "version": "1.4.5",
      "resolved": "https://registry.npmjs.org/@particle-network/connectors/-/connectors-1.4.5.tgz",
      "integrity": "sha512-bvPL7To7w0KYtkq34S/vjyLsiMEc6kXSgrp2S4LG6zoEvET4MQK2J7A5tDGmEl283QvD0K3LtmaCD43RwRPmUA==",
      "dependencies": {
        "@coinbase/wallet-sdk": "^3.7.1",
        "@particle-network/chains": "*",
        "@walletconnect/ethereum-provider": "~2.10.6",
        "@walletconnect/modal": "~2.6.2",
        "eventemitter3": "^4.0.0"
      },
      "engines": {
        "node": ">=16"
      }
    },
    "node_modules/@particle-network/connectors/node_modules/@walletconnect/core": {
      "version": "2.10.6",
      "resolved": "https://registry.npmjs.org/@walletconnect/core/-/core-2.10.6.tgz",
      "integrity": "sha512-Z4vh4ZdfcoQjgPEOxeuF9HUZCVLtV3MgRbS/awLIj/omDrFnOwlBhxi5Syr4Y8muVGC0ocRetQYHae0/gX5crQ==",
      "dependencies": {
        "@walletconnect/heartbeat": "1.2.1",
        "@walletconnect/jsonrpc-provider": "1.0.13",
        "@walletconnect/jsonrpc-types": "1.0.3",
        "@walletconnect/jsonrpc-utils": "1.0.8",
        "@walletconnect/jsonrpc-ws-connection": "1.0.14",
        "@walletconnect/keyvaluestorage": "^1.1.1",
        "@walletconnect/logger": "^2.0.1",
        "@walletconnect/relay-api": "^1.0.9",
        "@walletconnect/relay-auth": "^1.0.4",
        "@walletconnect/safe-json": "^1.0.2",
        "@walletconnect/time": "^1.0.2",
        "@walletconnect/types": "2.10.6",
        "@walletconnect/utils": "2.10.6",
        "events": "^3.3.0",
        "lodash.isequal": "4.5.0",
        "uint8arrays": "^3.1.0"
      }
    },
    "node_modules/@particle-network/connectors/node_modules/@walletconnect/ethereum-provider": {
      "version": "2.10.6",
      "resolved": "https://registry.npmjs.org/@walletconnect/ethereum-provider/-/ethereum-provider-2.10.6.tgz",
      "integrity": "sha512-bBQ+yUfxLv8VxNttgNKY7nED35gSVayO/BnLHbNKvyV1gpvSCla5mWB9MsXuQs70MK0g+/qtgRVSrOtdSubaNQ==",
      "dependencies": {
        "@walletconnect/jsonrpc-http-connection": "^1.0.7",
        "@walletconnect/jsonrpc-provider": "^1.0.13",
        "@walletconnect/jsonrpc-types": "^1.0.3",
        "@walletconnect/jsonrpc-utils": "^1.0.8",
        "@walletconnect/modal": "^2.4.3",
        "@walletconnect/sign-client": "2.10.6",
        "@walletconnect/types": "2.10.6",
        "@walletconnect/universal-provider": "2.10.6",
        "@walletconnect/utils": "2.10.6",
        "events": "^3.3.0"
      }
    },
    "node_modules/@particle-network/connectors/node_modules/@walletconnect/jsonrpc-provider": {
      "version": "1.0.13",
      "resolved": "https://registry.npmjs.org/@walletconnect/jsonrpc-provider/-/jsonrpc-provider-1.0.13.tgz",
      "integrity": "sha512-K73EpThqHnSR26gOyNEL+acEex3P7VWZe6KE12ZwKzAt2H4e5gldZHbjsu2QR9cLeJ8AXuO7kEMOIcRv1QEc7g==",
      "dependencies": {
        "@walletconnect/jsonrpc-utils": "^1.0.8",
        "@walletconnect/safe-json": "^1.0.2",
        "tslib": "1.14.1"
      }
    },
    "node_modules/@particle-network/connectors/node_modules/@walletconnect/jsonrpc-types": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/@walletconnect/jsonrpc-types/-/jsonrpc-types-1.0.3.tgz",
      "integrity": "sha512-iIQ8hboBl3o5ufmJ8cuduGad0CQm3ZlsHtujv9Eu16xq89q+BG7Nh5VLxxUgmtpnrePgFkTwXirCTkwJH1v+Yw==",
      "dependencies": {
        "keyvaluestorage-interface": "^1.0.0",
        "tslib": "1.14.1"
      }
    },
    "node_modules/@particle-network/connectors/node_modules/@walletconnect/jsonrpc-ws-connection": {
      "version": "1.0.14",
      "resolved": "https://registry.npmjs.org/@walletconnect/jsonrpc-ws-connection/-/jsonrpc-ws-connection-1.0.14.tgz",
      "integrity": "sha512-Jsl6fC55AYcbkNVkwNM6Jo+ufsuCQRqViOQ8ZBPH9pRREHH9welbBiszuTLqEJiQcO/6XfFDl6bzCJIkrEi8XA==",
      "dependencies": {
        "@walletconnect/jsonrpc-utils": "^1.0.6",
        "@walletconnect/safe-json": "^1.0.2",
        "events": "^3.3.0",
        "ws": "^7.5.1"
      }
    },
    "node_modules/@particle-network/connectors/node_modules/@walletconnect/sign-client": {
      "version": "2.10.6",
      "resolved": "https://registry.npmjs.org/@walletconnect/sign-client/-/sign-client-2.10.6.tgz",
      "integrity": "sha512-EvUWjaZBQu2yKnH5/5F2qzbuiIuUN9ZgrNKgvXkw5z1Dq5RJCks0S9/MFlKH/ZSGqXnLl7uAzBXtoX4sMgbCMA==",
      "deprecated": "Reliability and performance greatly improved - please see https://github.com/WalletConnect/walletconnect-monorepo/releases",
      "dependencies": {
        "@walletconnect/core": "2.10.6",
        "@walletconnect/events": "^1.0.1",
        "@walletconnect/heartbeat": "1.2.1",
        "@walletconnect/jsonrpc-utils": "1.0.8",
        "@walletconnect/logger": "^2.0.1",
        "@walletconnect/time": "^1.0.2",
        "@walletconnect/types": "2.10.6",
        "@walletconnect/utils": "2.10.6",
        "events": "^3.3.0"
      }
    },
    "node_modules/@particle-network/connectors/node_modules/@walletconnect/types": {
      "version": "2.10.6",
      "resolved": "https://registry.npmjs.org/@walletconnect/types/-/types-2.10.6.tgz",
      "integrity": "sha512-WgHfiTG1yakmxheaBRiXhUdEmgxwrvsAdOIWaMf/spvrzVKYh6sHI3oyEEky5qj5jjiMiyQBeB57QamzCotbcQ==",
      "dependencies": {
        "@walletconnect/events": "^1.0.1",
        "@walletconnect/heartbeat": "1.2.1",
        "@walletconnect/jsonrpc-types": "1.0.3",
        "@walletconnect/keyvaluestorage": "^1.1.1",
        "@walletconnect/logger": "^2.0.1",
        "events": "^3.3.0"
      }
    },
    "node_modules/@particle-network/connectors/node_modules/@walletconnect/universal-provider": {
      "version": "2.10.6",
      "resolved": "https://registry.npmjs.org/@walletconnect/universal-provider/-/universal-provider-2.10.6.tgz",
      "integrity": "sha512-CEivusqqoD31BhCTKp08DnrccfGjwD9MFjZs5BNRorDteRFE8zVm9LmP6DSiNJCw82ZajGlZThggLQ/BAATfwA==",
      "dependencies": {
        "@walletconnect/jsonrpc-http-connection": "^1.0.7",
        "@walletconnect/jsonrpc-provider": "1.0.13",
        "@walletconnect/jsonrpc-types": "^1.0.2",
        "@walletconnect/jsonrpc-utils": "^1.0.7",
        "@walletconnect/logger": "^2.0.1",
        "@walletconnect/sign-client": "2.10.6",
        "@walletconnect/types": "2.10.6",
        "@walletconnect/utils": "2.10.6",
        "events": "^3.3.0"
      }
    },
    "node_modules/@particle-network/connectors/node_modules/@walletconnect/utils": {
      "version": "2.10.6",
      "resolved": "https://registry.npmjs.org/@walletconnect/utils/-/utils-2.10.6.tgz",
      "integrity": "sha512-oRsWWhN2+hi3aiDXrQEOfysz6FHQJGXLsNQPVt+WIBJplO6Szmdau9dbleD88u1iiT4GKPqE0R9FOYvvPm1H/w==",
      "dependencies": {
        "@stablelib/chacha20poly1305": "1.0.1",
        "@stablelib/hkdf": "1.0.1",
        "@stablelib/random": "^1.0.2",
        "@stablelib/sha256": "1.0.1",
        "@stablelib/x25519": "^1.0.3",
        "@walletconnect/relay-api": "^1.0.9",
        "@walletconnect/safe-json": "^1.0.2",
        "@walletconnect/time": "^1.0.2",
        "@walletconnect/types": "2.10.6",
        "@walletconnect/window-getters": "^1.0.1",
        "@walletconnect/window-metadata": "^1.0.1",
        "detect-browser": "5.3.0",
        "query-string": "7.1.3",
        "uint8arrays": "^3.1.0"
      }
    },
    "node_modules/@particle-network/connectors/node_modules/ws": {
      "version": "7.5.10",
      "resolved": "https://registry.npmjs.org/ws/-/ws-7.5.10.tgz",
      "integrity": "sha512-+dbF1tHwZpXcbOJdVOkzLDxZP1ailvSxM6ZweXTegylPny803bFhA+vqBYw4s31NSAk4S2Qz+AKXK9a4wkdjcQ==",
      "engines": {
        "node": ">=8.3.0"
      },
      "peerDependencies": {
        "bufferutil": "^4.0.1",
        "utf-8-validate": "^5.0.2"
      },
      "peerDependenciesMeta": {
        "bufferutil": {
          "optional": true
        },
        "utf-8-validate": {
          "optional": true
        }
      }
    },
    "node_modules/@particle-network/thresh-sig": {
      "version": "0.7.8",
      "resolved": "https://registry.npmjs.org/@particle-network/thresh-sig/-/thresh-sig-0.7.8.tgz",
      "integrity": "sha512-Xe9yxt9s1ZnUpdwNPEHK9jMDg3Mjl9WePbmUMC4w7rZ+nxTE7gk0F+Q5mrEgwjmFAtDod0bCpzHygOOObF5QgQ==",
      "dependencies": {
        "@ethereumjs/tx": "^4.2.0",
        "@types/elliptic": "^6.4.14",
        "buffer": "^6.0.3",
        "elliptic": "^6.5.4"
      }
    },
    "node_modules/@particle-network/wallet": {
      "version": "1.4.6",
      "resolved": "https://registry.npmjs.org/@particle-network/wallet/-/wallet-1.4.6.tgz",
      "integrity": "sha512-ZpaKGuaA+xWL2jIgZikv9xyf/PGoKwlvPAj+XQR5QZn+KRfX318zbsn/RB0Wgu/vZ+tyY47zU/fqBS1NyJK/og==",
      "dependencies": {
        "@solana/web3.js": "^1.73.0",
        "crypto-js": "^4.1.1",
        "draggabilly": "^3.0.0",
        "fast-json-stable-stringify": "^2.1.0",
        "lodash": "^4.17.21",
        "uuid": "^9.0.1"
      },
      "engines": {
        "node": ">=16"
      }
    },
    "node_modules/@particle-network/wallet/node_modules/uuid": {
      "version": "9.0.1",
      "resolved": "https://registry.npmjs.org/uuid/-/uuid-9.0.1.tgz",
      "integrity": "sha512-b+1eJOlsR9K8HJpow9Ok3fiWOWSIcIzXodvv0rQjVoOVNpWMpxf1wZNpt4y9h10odCNrqnYp1OBzRktckBe3sA==",
      "funding": [
        "https://github.com/sponsors/broofa",
        "https://github.com/sponsors/ctavan"
      ],
      "bin": {
        "uuid": "dist/bin/uuid"
      }
    },
    "node_modules/@pkgjs/parseargs": {
      "version": "0.11.0",
      "resolved": "https://registry.npmjs.org/@pkgjs/parseargs/-/parseargs-0.11.0.tgz",
      "integrity": "sha512-+1VkjdD0QBLPodGrJUeqarH8VAIvQODIbwh9XpP5Syisf7YoQgsJKPNFoqqLQlu+VQ/tVSshMR6loPMn8U+dPg==",
      "dev": true,
      "optional": true,
      "engines": {
        "node": ">=14"
      }
    },
    "node_modules/@rc-component/portal": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/@rc-component/portal/-/portal-1.1.2.tgz",
      "integrity": "sha512-6f813C0IsasTZms08kfA8kPAGxbbkYToa8ALaiDIGGECU4i9hj8Plgbx0sNJDrey3EtHO30hmdaxtT0138xZcg==",
      "dependencies": {
        "@babel/runtime": "^7.18.0",
        "classnames": "^2.3.2",
        "rc-util": "^5.24.4"
      },
      "engines": {
        "node": ">=8.x"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/@remix-run/router": {
      "version": "1.20.0",
      "resolved": "https://registry.npmjs.org/@remix-run/router/-/router-1.20.0.tgz",
      "integrity": "sha512-mUnk8rPJBI9loFDZ+YzPGdeniYK+FTmRD1TMCz7ev2SNIozyKKpnGgsxO34u6Z4z/t0ITuu7voi/AshfsGsgFg==",
      "engines": {
        "node": ">=14.0.0"
      }
    },
    "node_modules/@rollup/rollup-android-arm-eabi": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-android-arm-eabi/-/rollup-android-arm-eabi-4.24.3.tgz",
      "integrity": "sha512-ufb2CH2KfBWPJok95frEZZ82LtDl0A6QKTa8MoM+cWwDZvVGl5/jNb79pIhRvAalUu+7LD91VYR0nwRD799HkQ==",
      "cpu": [
        "arm"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "android"
      ]
    },
    "node_modules/@rollup/rollup-android-arm64": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-android-arm64/-/rollup-android-arm64-4.24.3.tgz",
      "integrity": "sha512-iAHpft/eQk9vkWIV5t22V77d90CRofgR2006UiCjHcHJFVI1E0oBkQIAbz+pLtthFw3hWEmVB4ilxGyBf48i2Q==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "android"
      ]
    },
    "node_modules/@rollup/rollup-darwin-arm64": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-darwin-arm64/-/rollup-darwin-arm64-4.24.3.tgz",
      "integrity": "sha512-QPW2YmkWLlvqmOa2OwrfqLJqkHm7kJCIMq9kOz40Zo9Ipi40kf9ONG5Sz76zszrmIZZ4hgRIkez69YnTHgEz1w==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "darwin"
      ]
    },
    "node_modules/@rollup/rollup-darwin-x64": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-darwin-x64/-/rollup-darwin-x64-4.24.3.tgz",
      "integrity": "sha512-KO0pN5x3+uZm1ZXeIfDqwcvnQ9UEGN8JX5ufhmgH5Lz4ujjZMAnxQygZAVGemFWn+ZZC0FQopruV4lqmGMshow==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "darwin"
      ]
    },
    "node_modules/@rollup/rollup-freebsd-arm64": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-freebsd-arm64/-/rollup-freebsd-arm64-4.24.3.tgz",
      "integrity": "sha512-CsC+ZdIiZCZbBI+aRlWpYJMSWvVssPuWqrDy/zi9YfnatKKSLFCe6fjna1grHuo/nVaHG+kiglpRhyBQYRTK4A==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "freebsd"
      ]
    },
    "node_modules/@rollup/rollup-freebsd-x64": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-freebsd-x64/-/rollup-freebsd-x64-4.24.3.tgz",
      "integrity": "sha512-F0nqiLThcfKvRQhZEzMIXOQG4EeX61im61VYL1jo4eBxv4aZRmpin6crnBJQ/nWnCsjH5F6J3W6Stdm0mBNqBg==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "freebsd"
      ]
    },
    "node_modules/@rollup/rollup-linux-arm-gnueabihf": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-arm-gnueabihf/-/rollup-linux-arm-gnueabihf-4.24.3.tgz",
      "integrity": "sha512-KRSFHyE/RdxQ1CSeOIBVIAxStFC/hnBgVcaiCkQaVC+EYDtTe4X7z5tBkFyRoBgUGtB6Xg6t9t2kulnX6wJc6A==",
      "cpu": [
        "arm"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-arm-musleabihf": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-arm-musleabihf/-/rollup-linux-arm-musleabihf-4.24.3.tgz",
      "integrity": "sha512-h6Q8MT+e05zP5BxEKz0vi0DhthLdrNEnspdLzkoFqGwnmOzakEHSlXfVyA4HJ322QtFy7biUAVFPvIDEDQa6rw==",
      "cpu": [
        "arm"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-arm64-gnu": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-arm64-gnu/-/rollup-linux-arm64-gnu-4.24.3.tgz",
      "integrity": "sha512-fKElSyXhXIJ9pqiYRqisfirIo2Z5pTTve5K438URf08fsypXrEkVmShkSfM8GJ1aUyvjakT+fn2W7Czlpd/0FQ==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-arm64-musl": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-arm64-musl/-/rollup-linux-arm64-musl-4.24.3.tgz",
      "integrity": "sha512-YlddZSUk8G0px9/+V9PVilVDC6ydMz7WquxozToozSnfFK6wa6ne1ATUjUvjin09jp34p84milxlY5ikueoenw==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-powerpc64le-gnu": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-powerpc64le-gnu/-/rollup-linux-powerpc64le-gnu-4.24.3.tgz",
      "integrity": "sha512-yNaWw+GAO8JjVx3s3cMeG5Esz1cKVzz8PkTJSfYzE5u7A+NvGmbVFEHP+BikTIyYWuz0+DX9kaA3pH9Sqxp69g==",
      "cpu": [
        "ppc64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-riscv64-gnu": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-riscv64-gnu/-/rollup-linux-riscv64-gnu-4.24.3.tgz",
      "integrity": "sha512-lWKNQfsbpv14ZCtM/HkjCTm4oWTKTfxPmr7iPfp3AHSqyoTz5AgLemYkWLwOBWc+XxBbrU9SCokZP0WlBZM9lA==",
      "cpu": [
        "riscv64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-s390x-gnu": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-s390x-gnu/-/rollup-linux-s390x-gnu-4.24.3.tgz",
      "integrity": "sha512-HoojGXTC2CgCcq0Woc/dn12wQUlkNyfH0I1ABK4Ni9YXyFQa86Fkt2Q0nqgLfbhkyfQ6003i3qQk9pLh/SpAYw==",
      "cpu": [
        "s390x"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-x64-gnu": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-x64-gnu/-/rollup-linux-x64-gnu-4.24.3.tgz",
      "integrity": "sha512-mnEOh4iE4USSccBOtcrjF5nj+5/zm6NcNhbSEfR3Ot0pxBwvEn5QVUXcuOwwPkapDtGZ6pT02xLoPaNv06w7KQ==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-x64-musl": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-x64-musl/-/rollup-linux-x64-musl-4.24.3.tgz",
      "integrity": "sha512-rMTzawBPimBQkG9NKpNHvquIUTQPzrnPxPbCY1Xt+mFkW7pshvyIS5kYgcf74goxXOQk0CP3EoOC1zcEezKXhw==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-win32-arm64-msvc": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-win32-arm64-msvc/-/rollup-win32-arm64-msvc-4.24.3.tgz",
      "integrity": "sha512-2lg1CE305xNvnH3SyiKwPVsTVLCg4TmNCF1z7PSHX2uZY2VbUpdkgAllVoISD7JO7zu+YynpWNSKAtOrX3AiuA==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "win32"
      ]
    },
    "node_modules/@rollup/rollup-win32-ia32-msvc": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-win32-ia32-msvc/-/rollup-win32-ia32-msvc-4.24.3.tgz",
      "integrity": "sha512-9SjYp1sPyxJsPWuhOCX6F4jUMXGbVVd5obVpoVEi8ClZqo52ViZewA6eFz85y8ezuOA+uJMP5A5zo6Oz4S5rVQ==",
      "cpu": [
        "ia32"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "win32"
      ]
    },
    "node_modules/@rollup/rollup-win32-x64-msvc": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-win32-x64-msvc/-/rollup-win32-x64-msvc-4.24.3.tgz",
      "integrity": "sha512-HGZgRFFYrMrP3TJlq58nR1xy8zHKId25vhmm5S9jETEfDf6xybPxsavFTJaufe2zgOGYJBskGlj49CwtEuFhWQ==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "optional": true,
      "os": [
        "win32"
      ]
    },
    "node_modules/@scure/base": {
      "version": "1.1.9",
      "resolved": "https://registry.npmjs.org/@scure/base/-/base-1.1.9.tgz",
      "integrity": "sha512-8YKhl8GHiNI/pU2VMaofa2Tor7PJRAjwQLBBuilkJ9L5+13yVbC7JO/wS7piioAvPSwR3JKM1IJ/u4xQzbcXKg==",
      "funding": {
        "url": "https://paulmillr.com/funding/"
      }
    },
    "node_modules/@scure/bip32": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/@scure/bip32/-/bip32-1.4.0.tgz",
      "integrity": "sha512-sVUpc0Vq3tXCkDGYVWGIZTRfnvu8LoTDaev7vbwh0omSvVORONr960MQWdKqJDCReIEmTj3PAr73O3aoxz7OPg==",
      "dependencies": {
        "@noble/curves": "~1.4.0",
        "@noble/hashes": "~1.4.0",
        "@scure/base": "~1.1.6"
      },
      "funding": {
        "url": "https://paulmillr.com/funding/"
      }
    },
    "node_modules/@scure/bip32/node_modules/@noble/curves": {
      "version": "1.4.2",
      "resolved": "https://registry.npmjs.org/@noble/curves/-/curves-1.4.2.tgz",
      "integrity": "sha512-TavHr8qycMChk8UwMld0ZDRvatedkzWfH8IiaeGCfymOP5i0hSCozz9vHOL0nkwk7HRMlFnAiKpS2jrUmSybcw==",
      "dependencies": {
        "@noble/hashes": "1.4.0"
      },
      "funding": {
        "url": "https://paulmillr.com/funding/"
      }
    },
    "node_modules/@scure/bip32/node_modules/@noble/hashes": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/@noble/hashes/-/hashes-1.4.0.tgz",
      "integrity": "sha512-V1JJ1WTRUqHHrOSh597hURcMqVKVGL/ea3kv0gSnEdsEZ0/+VyPghM1lMNGc00z7CIQorSvbKpuJkxvuHbvdbg==",
      "engines": {
        "node": ">= 16"
      },
      "funding": {
        "url": "https://paulmillr.com/funding/"
      }
    },
    "node_modules/@scure/bip39": {
      "version": "1.3.0",
      "resolved": "https://registry.npmjs.org/@scure/bip39/-/bip39-1.3.0.tgz",
      "integrity": "sha512-disdg7gHuTDZtY+ZdkmLpPCk7fxZSu3gBiEGuoC1XYxv9cGx3Z6cpTggCgW6odSOOIXCiDjuGejW+aJKCY/pIQ==",
      "dependencies": {
        "@noble/hashes": "~1.4.0",
        "@scure/base": "~1.1.6"
      },
      "funding": {
        "url": "https://paulmillr.com/funding/"
      }
    },
    "node_modules/@scure/bip39/node_modules/@noble/hashes": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/@noble/hashes/-/hashes-1.4.0.tgz",
      "integrity": "sha512-V1JJ1WTRUqHHrOSh597hURcMqVKVGL/ea3kv0gSnEdsEZ0/+VyPghM1lMNGc00z7CIQorSvbKpuJkxvuHbvdbg==",
      "engines": {
        "node": ">= 16"
      },
      "funding": {
        "url": "https://paulmillr.com/funding/"
      }
    },
    "node_modules/@sideway/address": {
      "version": "4.1.5",
      "resolved": "https://registry.npmjs.org/@sideway/address/-/address-4.1.5.tgz",
      "integrity": "sha512-IqO/DUQHUkPeixNQ8n0JA6102hT9CmaljNTPmQ1u8MEhBo/R4Q8eKLN/vGZxuebwOroDB4cbpjheD4+/sKFK4Q==",
      "dependencies": {
        "@hapi/hoek": "^9.0.0"
      }
    },
    "node_modules/@sideway/formula": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/@sideway/formula/-/formula-3.0.1.tgz",
      "integrity": "sha512-/poHZJJVjx3L+zVD6g9KgHfYnb443oi7wLu/XKojDviHy6HOEOA6z1Trk5aR1dGcmPenJEgb2sK2I80LeS3MIg=="
    },
    "node_modules/@sideway/pinpoint": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/@sideway/pinpoint/-/pinpoint-2.0.0.tgz",
      "integrity": "sha512-RNiOoTPkptFtSVzQevY/yWtZwf/RxyVnPy/OcA9HBM3MlGDnBEYL5B41H0MTn0Uec8Hi+2qUtTfG2WWZBmMejQ=="
    },
    "node_modules/@smithy/abort-controller": {
      "version": "3.1.6",
      "resolved": "https://registry.npmjs.org/@smithy/abort-controller/-/abort-controller-3.1.6.tgz",
      "integrity": "sha512-0XuhuHQlEqbNQZp7QxxrFTdVWdwxch4vjxYgfInF91hZFkPxf9QDrdQka0KfxFMPqLNzSw0b95uGTrLliQUavQ==",
      "dependencies": {
        "@smithy/types": "^3.6.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/abort-controller/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/config-resolver": {
      "version": "3.0.10",
      "resolved": "https://registry.npmjs.org/@smithy/config-resolver/-/config-resolver-3.0.10.tgz",
      "integrity": "sha512-Uh0Sz9gdUuz538nvkPiyv1DZRX9+D15EKDtnQP5rYVAzM/dnYk3P8cg73jcxyOitPgT3mE3OVj7ky7sibzHWkw==",
      "dependencies": {
        "@smithy/node-config-provider": "^3.1.9",
        "@smithy/types": "^3.6.0",
        "@smithy/util-config-provider": "^3.0.0",
        "@smithy/util-middleware": "^3.0.8",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/config-resolver/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/core": {
      "version": "2.5.1",
      "resolved": "https://registry.npmjs.org/@smithy/core/-/core-2.5.1.tgz",
      "integrity": "sha512-DujtuDA7BGEKExJ05W5OdxCoyekcKT3Rhg1ZGeiUWaz2BJIWXjZmsG/DIP4W48GHno7AQwRsaCb8NcBgH3QZpg==",
      "dependencies": {
        "@smithy/middleware-serde": "^3.0.8",
        "@smithy/protocol-http": "^4.1.5",
        "@smithy/types": "^3.6.0",
        "@smithy/util-body-length-browser": "^3.0.0",
        "@smithy/util-middleware": "^3.0.8",
        "@smithy/util-stream": "^3.2.1",
        "@smithy/util-utf8": "^3.0.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/core/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/credential-provider-imds": {
      "version": "3.2.5",
      "resolved": "https://registry.npmjs.org/@smithy/credential-provider-imds/-/credential-provider-imds-3.2.5.tgz",
      "integrity": "sha512-4FTQGAsuwqTzVMmiRVTn0RR9GrbRfkP0wfu/tXWVHd2LgNpTY0uglQpIScXK4NaEyXbB3JmZt8gfVqO50lP8wg==",
      "dependencies": {
        "@smithy/node-config-provider": "^3.1.9",
        "@smithy/property-provider": "^3.1.8",
        "@smithy/types": "^3.6.0",
        "@smithy/url-parser": "^3.0.8",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/credential-provider-imds/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/fetch-http-handler": {
      "version": "3.2.9",
      "resolved": "https://registry.npmjs.org/@smithy/fetch-http-handler/-/fetch-http-handler-3.2.9.tgz",
      "integrity": "sha512-hYNVQOqhFQ6vOpenifFME546f0GfJn2OiQ3M0FDmuUu8V/Uiwy2wej7ZXxFBNqdx0R5DZAqWM1l6VRhGz8oE6A==",
      "dependencies": {
        "@smithy/protocol-http": "^4.1.4",
        "@smithy/querystring-builder": "^3.0.7",
        "@smithy/types": "^3.5.0",
        "@smithy/util-base64": "^3.0.0",
        "tslib": "^2.6.2"
      }
    },
    "node_modules/@smithy/fetch-http-handler/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/hash-node": {
      "version": "3.0.8",
      "resolved": "https://registry.npmjs.org/@smithy/hash-node/-/hash-node-3.0.8.tgz",
      "integrity": "sha512-tlNQYbfpWXHimHqrvgo14DrMAgUBua/cNoz9fMYcDmYej7MAmUcjav/QKQbFc3NrcPxeJ7QClER4tWZmfwoPng==",
      "dependencies": {
        "@smithy/types": "^3.6.0",
        "@smithy/util-buffer-from": "^3.0.0",
        "@smithy/util-utf8": "^3.0.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/hash-node/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/invalid-dependency": {
      "version": "3.0.8",
      "resolved": "https://registry.npmjs.org/@smithy/invalid-dependency/-/invalid-dependency-3.0.8.tgz",
      "integrity": "sha512-7Qynk6NWtTQhnGTTZwks++nJhQ1O54Mzi7fz4PqZOiYXb4Z1Flpb2yRvdALoggTS8xjtohWUM+RygOtB30YL3Q==",
      "dependencies": {
        "@smithy/types": "^3.6.0",
        "tslib": "^2.6.2"
      }
    },
    "node_modules/@smithy/invalid-dependency/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/is-array-buffer": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/@smithy/is-array-buffer/-/is-array-buffer-3.0.0.tgz",
      "integrity": "sha512-+Fsu6Q6C4RSJiy81Y8eApjEB5gVtM+oFKTffg+jSuwtvomJJrhUJBu2zS8wjXSgH/g1MKEWrzyChTBe6clb5FQ==",
      "dependencies": {
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/is-array-buffer/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/middleware-content-length": {
      "version": "3.0.10",
      "resolved": "https://registry.npmjs.org/@smithy/middleware-content-length/-/middleware-content-length-3.0.10.tgz",
      "integrity": "sha512-T4dIdCs1d/+/qMpwhJ1DzOhxCZjZHbHazEPJWdB4GDi2HjIZllVzeBEcdJUN0fomV8DURsgOyrbEUzg3vzTaOg==",
      "dependencies": {
        "@smithy/protocol-http": "^4.1.5",
        "@smithy/types": "^3.6.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/middleware-content-length/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/middleware-endpoint": {
      "version": "3.2.1",
      "resolved": "https://registry.npmjs.org/@smithy/middleware-endpoint/-/middleware-endpoint-3.2.1.tgz",
      "integrity": "sha512-wWO3xYmFm6WRW8VsEJ5oU6h7aosFXfszlz3Dj176pTij6o21oZnzkCLzShfmRaaCHDkBXWBdO0c4sQAvLFP6zA==",
      "dependencies": {
        "@smithy/core": "^2.5.1",
        "@smithy/middleware-serde": "^3.0.8",
        "@smithy/node-config-provider": "^3.1.9",
        "@smithy/shared-ini-file-loader": "^3.1.9",
        "@smithy/types": "^3.6.0",
        "@smithy/url-parser": "^3.0.8",
        "@smithy/util-middleware": "^3.0.8",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/middleware-endpoint/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/middleware-retry": {
      "version": "3.0.25",
      "resolved": "https://registry.npmjs.org/@smithy/middleware-retry/-/middleware-retry-3.0.25.tgz",
      "integrity": "sha512-m1F70cPaMBML4HiTgCw5I+jFNtjgz5z5UdGnUbG37vw6kh4UvizFYjqJGHvicfgKMkDL6mXwyPp5mhZg02g5sg==",
      "dependencies": {
        "@smithy/node-config-provider": "^3.1.9",
        "@smithy/protocol-http": "^4.1.5",
        "@smithy/service-error-classification": "^3.0.8",
        "@smithy/smithy-client": "^3.4.2",
        "@smithy/types": "^3.6.0",
        "@smithy/util-middleware": "^3.0.8",
        "@smithy/util-retry": "^3.0.8",
        "tslib": "^2.6.2",
        "uuid": "^9.0.1"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/middleware-retry/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/middleware-retry/node_modules/uuid": {
      "version": "9.0.1",
      "resolved": "https://registry.npmjs.org/uuid/-/uuid-9.0.1.tgz",
      "integrity": "sha512-b+1eJOlsR9K8HJpow9Ok3fiWOWSIcIzXodvv0rQjVoOVNpWMpxf1wZNpt4y9h10odCNrqnYp1OBzRktckBe3sA==",
      "funding": [
        "https://github.com/sponsors/broofa",
        "https://github.com/sponsors/ctavan"
      ],
      "bin": {
        "uuid": "dist/bin/uuid"
      }
    },
    "node_modules/@smithy/middleware-serde": {
      "version": "3.0.8",
      "resolved": "https://registry.npmjs.org/@smithy/middleware-serde/-/middleware-serde-3.0.8.tgz",
      "integrity": "sha512-Xg2jK9Wc/1g/MBMP/EUn2DLspN8LNt+GMe7cgF+Ty3vl+Zvu+VeZU5nmhveU+H8pxyTsjrAkci8NqY6OuvZnjA==",
      "dependencies": {
        "@smithy/types": "^3.6.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/middleware-serde/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/middleware-stack": {
      "version": "3.0.8",
      "resolved": "https://registry.npmjs.org/@smithy/middleware-stack/-/middleware-stack-3.0.8.tgz",
      "integrity": "sha512-d7ZuwvYgp1+3682Nx0MD3D/HtkmZd49N3JUndYWQXfRZrYEnCWYc8BHcNmVsPAp9gKvlurdg/mubE6b/rPS9MA==",
      "dependencies": {
        "@smithy/types": "^3.6.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/middleware-stack/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/node-config-provider": {
      "version": "3.1.9",
      "resolved": "https://registry.npmjs.org/@smithy/node-config-provider/-/node-config-provider-3.1.9.tgz",
      "integrity": "sha512-qRHoah49QJ71eemjuS/WhUXB+mpNtwHRWQr77J/m40ewBVVwvo52kYAmb7iuaECgGTTcYxHS4Wmewfwy++ueew==",
      "dependencies": {
        "@smithy/property-provider": "^3.1.8",
        "@smithy/shared-ini-file-loader": "^3.1.9",
        "@smithy/types": "^3.6.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/node-config-provider/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/node-http-handler": {
      "version": "3.2.5",
      "resolved": "https://registry.npmjs.org/@smithy/node-http-handler/-/node-http-handler-3.2.5.tgz",
      "integrity": "sha512-PkOwPNeKdvX/jCpn0A8n9/TyoxjGZB8WVoJmm9YzsnAgggTj4CrjpRHlTQw7dlLZ320n1mY1y+nTRUDViKi/3w==",
      "dependencies": {
        "@smithy/abort-controller": "^3.1.6",
        "@smithy/protocol-http": "^4.1.5",
        "@smithy/querystring-builder": "^3.0.8",
        "@smithy/types": "^3.6.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/node-http-handler/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/property-provider": {
      "version": "3.1.8",
      "resolved": "https://registry.npmjs.org/@smithy/property-provider/-/property-provider-3.1.8.tgz",
      "integrity": "sha512-ukNUyo6rHmusG64lmkjFeXemwYuKge1BJ8CtpVKmrxQxc6rhUX0vebcptFA9MmrGsnLhwnnqeH83VTU9hwOpjA==",
      "dependencies": {
        "@smithy/types": "^3.6.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/property-provider/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/protocol-http": {
      "version": "4.1.5",
      "resolved": "https://registry.npmjs.org/@smithy/protocol-http/-/protocol-http-4.1.5.tgz",
      "integrity": "sha512-hsjtwpIemmCkm3ZV5fd/T0bPIugW1gJXwZ/hpuVubt2hEUApIoUTrf6qIdh9MAWlw0vjMrA1ztJLAwtNaZogvg==",
      "dependencies": {
        "@smithy/types": "^3.6.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/protocol-http/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/querystring-builder": {
      "version": "3.0.8",
      "resolved": "https://registry.npmjs.org/@smithy/querystring-builder/-/querystring-builder-3.0.8.tgz",
      "integrity": "sha512-btYxGVqFUARbUrN6VhL9c3dnSviIwBYD9Rz1jHuN1hgh28Fpv2xjU1HeCeDJX68xctz7r4l1PBnFhGg1WBBPuA==",
      "dependencies": {
        "@smithy/types": "^3.6.0",
        "@smithy/util-uri-escape": "^3.0.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/querystring-builder/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/querystring-parser": {
      "version": "3.0.8",
      "resolved": "https://registry.npmjs.org/@smithy/querystring-parser/-/querystring-parser-3.0.8.tgz",
      "integrity": "sha512-BtEk3FG7Ks64GAbt+JnKqwuobJNX8VmFLBsKIwWr1D60T426fGrV2L3YS5siOcUhhp6/Y6yhBw1PSPxA5p7qGg==",
      "dependencies": {
        "@smithy/types": "^3.6.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/querystring-parser/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/service-error-classification": {
      "version": "3.0.8",
      "resolved": "https://registry.npmjs.org/@smithy/service-error-classification/-/service-error-classification-3.0.8.tgz",
      "integrity": "sha512-uEC/kCCFto83bz5ZzapcrgGqHOh/0r69sZ2ZuHlgoD5kYgXJEThCoTuw/y1Ub3cE7aaKdznb+jD9xRPIfIwD7g==",
      "dependencies": {
        "@smithy/types": "^3.6.0"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/shared-ini-file-loader": {
      "version": "3.1.9",
      "resolved": "https://registry.npmjs.org/@smithy/shared-ini-file-loader/-/shared-ini-file-loader-3.1.9.tgz",
      "integrity": "sha512-/+OsJRNtoRbtsX0UpSgWVxFZLsJHo/4sTr+kBg/J78sr7iC+tHeOvOJrS5hCpVQ6sWBbhWLp1UNiuMyZhE6pmA==",
      "dependencies": {
        "@smithy/types": "^3.6.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/shared-ini-file-loader/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/signature-v4": {
      "version": "4.2.1",
      "resolved": "https://registry.npmjs.org/@smithy/signature-v4/-/signature-v4-4.2.1.tgz",
      "integrity": "sha512-NsV1jF4EvmO5wqmaSzlnTVetemBS3FZHdyc5CExbDljcyJCEEkJr8ANu2JvtNbVg/9MvKAWV44kTrGS+Pi4INg==",
      "dependencies": {
        "@smithy/is-array-buffer": "^3.0.0",
        "@smithy/protocol-http": "^4.1.5",
        "@smithy/types": "^3.6.0",
        "@smithy/util-hex-encoding": "^3.0.0",
        "@smithy/util-middleware": "^3.0.8",
        "@smithy/util-uri-escape": "^3.0.0",
        "@smithy/util-utf8": "^3.0.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/signature-v4/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/smithy-client": {
      "version": "3.4.2",
      "resolved": "https://registry.npmjs.org/@smithy/smithy-client/-/smithy-client-3.4.2.tgz",
      "integrity": "sha512-dxw1BDxJiY9/zI3cBqfVrInij6ShjpV4fmGHesGZZUiP9OSE/EVfdwdRz0PgvkEvrZHpsj2htRaHJfftE8giBA==",
      "dependencies": {
        "@smithy/core": "^2.5.1",
        "@smithy/middleware-endpoint": "^3.2.1",
        "@smithy/middleware-stack": "^3.0.8",
        "@smithy/protocol-http": "^4.1.5",
        "@smithy/types": "^3.6.0",
        "@smithy/util-stream": "^3.2.1",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/smithy-client/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/types": {
      "version": "3.6.0",
      "resolved": "https://registry.npmjs.org/@smithy/types/-/types-3.6.0.tgz",
      "integrity": "sha512-8VXK/KzOHefoC65yRgCn5vG1cysPJjHnOVt9d0ybFQSmJgQj152vMn4EkYhGuaOmnnZvCPav/KnYyE6/KsNZ2w==",
      "dependencies": {
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/types/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/url-parser": {
      "version": "3.0.8",
      "resolved": "https://registry.npmjs.org/@smithy/url-parser/-/url-parser-3.0.8.tgz",
      "integrity": "sha512-4FdOhwpTW7jtSFWm7SpfLGKIBC9ZaTKG5nBF0wK24aoQKQyDIKUw3+KFWCQ9maMzrgTJIuOvOnsV2lLGW5XjTg==",
      "dependencies": {
        "@smithy/querystring-parser": "^3.0.8",
        "@smithy/types": "^3.6.0",
        "tslib": "^2.6.2"
      }
    },
    "node_modules/@smithy/url-parser/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/util-base64": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/@smithy/util-base64/-/util-base64-3.0.0.tgz",
      "integrity": "sha512-Kxvoh5Qtt0CDsfajiZOCpJxgtPHXOKwmM+Zy4waD43UoEMA+qPxxa98aE/7ZhdnBFZFXMOiBR5xbcaMhLtznQQ==",
      "dependencies": {
        "@smithy/util-buffer-from": "^3.0.0",
        "@smithy/util-utf8": "^3.0.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/util-base64/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/util-body-length-browser": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/@smithy/util-body-length-browser/-/util-body-length-browser-3.0.0.tgz",
      "integrity": "sha512-cbjJs2A1mLYmqmyVl80uoLTJhAcfzMOyPgjwAYusWKMdLeNtzmMz9YxNl3/jRLoxSS3wkqkf0jwNdtXWtyEBaQ==",
      "dependencies": {
        "tslib": "^2.6.2"
      }
    },
    "node_modules/@smithy/util-body-length-browser/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/util-body-length-node": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/@smithy/util-body-length-node/-/util-body-length-node-3.0.0.tgz",
      "integrity": "sha512-Tj7pZ4bUloNUP6PzwhN7K386tmSmEET9QtQg0TgdNOnxhZvCssHji+oZTUIuzxECRfG8rdm2PMw2WCFs6eIYkA==",
      "dependencies": {
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/util-body-length-node/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/util-buffer-from": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/@smithy/util-buffer-from/-/util-buffer-from-3.0.0.tgz",
      "integrity": "sha512-aEOHCgq5RWFbP+UDPvPot26EJHjOC+bRgse5A8V3FSShqd5E5UN4qc7zkwsvJPPAVsf73QwYcHN1/gt/rtLwQA==",
      "dependencies": {
        "@smithy/is-array-buffer": "^3.0.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/util-buffer-from/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/util-config-provider": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/@smithy/util-config-provider/-/util-config-provider-3.0.0.tgz",
      "integrity": "sha512-pbjk4s0fwq3Di/ANL+rCvJMKM5bzAQdE5S/6RL5NXgMExFAi6UgQMPOm5yPaIWPpr+EOXKXRonJ3FoxKf4mCJQ==",
      "dependencies": {
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/util-config-provider/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/util-defaults-mode-browser": {
      "version": "3.0.25",
      "resolved": "https://registry.npmjs.org/@smithy/util-defaults-mode-browser/-/util-defaults-mode-browser-3.0.25.tgz",
      "integrity": "sha512-fRw7zymjIDt6XxIsLwfJfYUfbGoO9CmCJk6rjJ/X5cd20+d2Is7xjU5Kt/AiDt6hX8DAf5dztmfP5O82gR9emA==",
      "dependencies": {
        "@smithy/property-provider": "^3.1.8",
        "@smithy/smithy-client": "^3.4.2",
        "@smithy/types": "^3.6.0",
        "bowser": "^2.11.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">= 10.0.0"
      }
    },
    "node_modules/@smithy/util-defaults-mode-browser/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/util-defaults-mode-node": {
      "version": "3.0.25",
      "resolved": "https://registry.npmjs.org/@smithy/util-defaults-mode-node/-/util-defaults-mode-node-3.0.25.tgz",
      "integrity": "sha512-H3BSZdBDiVZGzt8TG51Pd2FvFO0PAx/A0mJ0EH8a13KJ6iUCdYnw/Dk/MdC1kTd0eUuUGisDFaxXVXo4HHFL1g==",
      "dependencies": {
        "@smithy/config-resolver": "^3.0.10",
        "@smithy/credential-provider-imds": "^3.2.5",
        "@smithy/node-config-provider": "^3.1.9",
        "@smithy/property-provider": "^3.1.8",
        "@smithy/smithy-client": "^3.4.2",
        "@smithy/types": "^3.6.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">= 10.0.0"
      }
    },
    "node_modules/@smithy/util-defaults-mode-node/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/util-endpoints": {
      "version": "2.1.4",
      "resolved": "https://registry.npmjs.org/@smithy/util-endpoints/-/util-endpoints-2.1.4.tgz",
      "integrity": "sha512-kPt8j4emm7rdMWQyL0F89o92q10gvCUa6sBkBtDJ7nV2+P7wpXczzOfoDJ49CKXe5CCqb8dc1W+ZdLlrKzSAnQ==",
      "dependencies": {
        "@smithy/node-config-provider": "^3.1.9",
        "@smithy/types": "^3.6.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/util-endpoints/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/util-hex-encoding": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/@smithy/util-hex-encoding/-/util-hex-encoding-3.0.0.tgz",
      "integrity": "sha512-eFndh1WEK5YMUYvy3lPlVmYY/fZcQE1D8oSf41Id2vCeIkKJXPcYDCZD+4+xViI6b1XSd7tE+s5AmXzz5ilabQ==",
      "dependencies": {
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/util-hex-encoding/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/util-middleware": {
      "version": "3.0.8",
      "resolved": "https://registry.npmjs.org/@smithy/util-middleware/-/util-middleware-3.0.8.tgz",
      "integrity": "sha512-p7iYAPaQjoeM+AKABpYWeDdtwQNxasr4aXQEA/OmbOaug9V0odRVDy3Wx4ci8soljE/JXQo+abV0qZpW8NX0yA==",
      "dependencies": {
        "@smithy/types": "^3.6.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/util-middleware/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/util-retry": {
      "version": "3.0.8",
      "resolved": "https://registry.npmjs.org/@smithy/util-retry/-/util-retry-3.0.8.tgz",
      "integrity": "sha512-TCEhLnY581YJ+g1x0hapPz13JFqzmh/pMWL2KEFASC51qCfw3+Y47MrTmea4bUE5vsdxQ4F6/KFbUeSz22Q1ow==",
      "dependencies": {
        "@smithy/service-error-classification": "^3.0.8",
        "@smithy/types": "^3.6.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/util-retry/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/util-stream": {
      "version": "3.2.1",
      "resolved": "https://registry.npmjs.org/@smithy/util-stream/-/util-stream-3.2.1.tgz",
      "integrity": "sha512-R3ufuzJRxSJbE58K9AEnL/uSZyVdHzud9wLS8tIbXclxKzoe09CRohj2xV8wpx5tj7ZbiJaKYcutMm1eYgz/0A==",
      "dependencies": {
        "@smithy/fetch-http-handler": "^4.0.0",
        "@smithy/node-http-handler": "^3.2.5",
        "@smithy/types": "^3.6.0",
        "@smithy/util-base64": "^3.0.0",
        "@smithy/util-buffer-from": "^3.0.0",
        "@smithy/util-hex-encoding": "^3.0.0",
        "@smithy/util-utf8": "^3.0.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/util-stream/node_modules/@smithy/fetch-http-handler": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/@smithy/fetch-http-handler/-/fetch-http-handler-4.0.0.tgz",
      "integrity": "sha512-MLb1f5tbBO2X6K4lMEKJvxeLooyg7guq48C2zKr4qM7F2Gpkz4dc+hdSgu77pCJ76jVqFBjZczHYAs6dp15N+g==",
      "dependencies": {
        "@smithy/protocol-http": "^4.1.5",
        "@smithy/querystring-builder": "^3.0.8",
        "@smithy/types": "^3.6.0",
        "@smithy/util-base64": "^3.0.0",
        "tslib": "^2.6.2"
      }
    },
    "node_modules/@smithy/util-stream/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/util-uri-escape": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/@smithy/util-uri-escape/-/util-uri-escape-3.0.0.tgz",
      "integrity": "sha512-LqR7qYLgZTD7nWLBecUi4aqolw8Mhza9ArpNEQ881MJJIU2sE5iHCK6TdyqqzcDLy0OPe10IY4T8ctVdtynubg==",
      "dependencies": {
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/util-uri-escape/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@smithy/util-utf8": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/@smithy/util-utf8/-/util-utf8-3.0.0.tgz",
      "integrity": "sha512-rUeT12bxFnplYDe815GXbq/oixEGHfRFFtcTF3YdDi/JaENIM6aSYYLJydG83UNzLXeRI5K8abYd/8Sp/QM0kA==",
      "dependencies": {
        "@smithy/util-buffer-from": "^3.0.0",
        "tslib": "^2.6.2"
      },
      "engines": {
        "node": ">=16.0.0"
      }
    },
    "node_modules/@smithy/util-utf8/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@solana/buffer-layout": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/@solana/buffer-layout/-/buffer-layout-4.0.1.tgz",
      "integrity": "sha512-E1ImOIAD1tBZFRdjeM4/pzTiTApC0AOBGwyAMS4fwIodCWArzJ3DWdoh8cKxeFM2fElkxBh2Aqts1BPC373rHA==",
      "dependencies": {
        "buffer": "~6.0.3"
      },
      "engines": {
        "node": ">=5.10"
      }
    },
    "node_modules/@solana/buffer-layout-utils": {
      "version": "0.2.0",
      "resolved": "https://registry.npmjs.org/@solana/buffer-layout-utils/-/buffer-layout-utils-0.2.0.tgz",
      "integrity": "sha512-szG4sxgJGktbuZYDg2FfNmkMi0DYQoVjN2h7ta1W1hPrwzarcFLBq9UpX1UjNXsNpT9dn+chgprtWGioUAr4/g==",
      "dependencies": {
        "@solana/buffer-layout": "^4.0.0",
        "@solana/web3.js": "^1.32.0",
        "bigint-buffer": "^1.1.5",
        "bignumber.js": "^9.0.1"
      },
      "engines": {
        "node": ">= 10"
      }
    },
    "node_modules/@solana/spl-token": {
      "version": "0.2.0",
      "resolved": "https://registry.npmjs.org/@solana/spl-token/-/spl-token-0.2.0.tgz",
      "integrity": "sha512-RWcn31OXtdqIxmkzQfB2R+WpsJOVS6rKuvpxJFjvik2LyODd+WN58ZP3Rpjpro03fscGAkzlFuP3r42doRJgyQ==",
      "dependencies": {
        "@solana/buffer-layout": "^4.0.0",
        "@solana/buffer-layout-utils": "^0.2.0",
        "@solana/web3.js": "^1.32.0",
        "start-server-and-test": "^1.14.0"
      },
      "engines": {
        "node": ">= 14"
      }
    },
    "node_modules/@solana/web3.js": {
      "version": "1.95.4",
      "resolved": "https://registry.npmjs.org/@solana/web3.js/-/web3.js-1.95.4.tgz",
      "integrity": "sha512-sdewnNEA42ZSMxqkzdwEWi6fDgzwtJHaQa5ndUGEJYtoOnM6X5cvPmjoTUp7/k7bRrVAxfBgDnvQQHD6yhlLYw==",
      "dependencies": {
        "@babel/runtime": "^7.25.0",
        "@noble/curves": "^1.4.2",
        "@noble/hashes": "^1.4.0",
        "@solana/buffer-layout": "^4.0.1",
        "agentkeepalive": "^4.5.0",
        "bigint-buffer": "^1.1.5",
        "bn.js": "^5.2.1",
        "borsh": "^0.7.0",
        "bs58": "^4.0.1",
        "buffer": "6.0.3",
        "fast-stable-stringify": "^1.0.0",
        "jayson": "^4.1.1",
        "node-fetch": "^2.7.0",
        "rpc-websockets": "^9.0.2",
        "superstruct": "^2.0.2"
      }
    },
    "node_modules/@stablelib/aead": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@stablelib/aead/-/aead-1.0.1.tgz",
      "integrity": "sha512-q39ik6sxGHewqtO0nP4BuSe3db5G1fEJE8ukvngS2gLkBXyy6E7pLubhbYgnkDFv6V8cWaxcE4Xn0t6LWcJkyg=="
    },
    "node_modules/@stablelib/binary": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@stablelib/binary/-/binary-1.0.1.tgz",
      "integrity": "sha512-ClJWvmL6UBM/wjkvv/7m5VP3GMr9t0osr4yVgLZsLCOz4hGN9gIAFEqnJ0TsSMAN+n840nf2cHZnA5/KFqHC7Q==",
      "dependencies": {
        "@stablelib/int": "^1.0.1"
      }
    },
    "node_modules/@stablelib/bytes": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@stablelib/bytes/-/bytes-1.0.1.tgz",
      "integrity": "sha512-Kre4Y4kdwuqL8BR2E9hV/R5sOrUj6NanZaZis0V6lX5yzqC3hBuVSDXUIBqQv/sCpmuWRiHLwqiT1pqqjuBXoQ=="
    },
    "node_modules/@stablelib/chacha": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@stablelib/chacha/-/chacha-1.0.1.tgz",
      "integrity": "sha512-Pmlrswzr0pBzDofdFuVe1q7KdsHKhhU24e8gkEwnTGOmlC7PADzLVxGdn2PoNVBBabdg0l/IfLKg6sHAbTQugg==",
      "dependencies": {
        "@stablelib/binary": "^1.0.1",
        "@stablelib/wipe": "^1.0.1"
      }
    },
    "node_modules/@stablelib/chacha20poly1305": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@stablelib/chacha20poly1305/-/chacha20poly1305-1.0.1.tgz",
      "integrity": "sha512-MmViqnqHd1ymwjOQfghRKw2R/jMIGT3wySN7cthjXCBdO+qErNPUBnRzqNpnvIwg7JBCg3LdeCZZO4de/yEhVA==",
      "dependencies": {
        "@stablelib/aead": "^1.0.1",
        "@stablelib/binary": "^1.0.1",
        "@stablelib/chacha": "^1.0.1",
        "@stablelib/constant-time": "^1.0.1",
        "@stablelib/poly1305": "^1.0.1",
        "@stablelib/wipe": "^1.0.1"
      }
    },
    "node_modules/@stablelib/constant-time": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@stablelib/constant-time/-/constant-time-1.0.1.tgz",
      "integrity": "sha512-tNOs3uD0vSJcK6z1fvef4Y+buN7DXhzHDPqRLSXUel1UfqMB1PWNsnnAezrKfEwTLpN0cGH2p9NNjs6IqeD0eg=="
    },
    "node_modules/@stablelib/ed25519": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/@stablelib/ed25519/-/ed25519-1.0.3.tgz",
      "integrity": "sha512-puIMWaX9QlRsbhxfDc5i+mNPMY+0TmQEskunY1rZEBPi1acBCVQAhnsk/1Hk50DGPtVsZtAWQg4NHGlVaO9Hqg==",
      "dependencies": {
        "@stablelib/random": "^1.0.2",
        "@stablelib/sha512": "^1.0.1",
        "@stablelib/wipe": "^1.0.1"
      }
    },
    "node_modules/@stablelib/hash": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@stablelib/hash/-/hash-1.0.1.tgz",
      "integrity": "sha512-eTPJc/stDkdtOcrNMZ6mcMK1e6yBbqRBaNW55XA1jU8w/7QdnCF0CmMmOD1m7VSkBR44PWrMHU2l6r8YEQHMgg=="
    },
    "node_modules/@stablelib/hkdf": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@stablelib/hkdf/-/hkdf-1.0.1.tgz",
      "integrity": "sha512-SBEHYE16ZXlHuaW5RcGk533YlBj4grMeg5TooN80W3NpcHRtLZLLXvKyX0qcRFxf+BGDobJLnwkvgEwHIDBR6g==",
      "dependencies": {
        "@stablelib/hash": "^1.0.1",
        "@stablelib/hmac": "^1.0.1",
        "@stablelib/wipe": "^1.0.1"
      }
    },
    "node_modules/@stablelib/hmac": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@stablelib/hmac/-/hmac-1.0.1.tgz",
      "integrity": "sha512-V2APD9NSnhVpV/QMYgCVMIYKiYG6LSqw1S65wxVoirhU/51ACio6D4yDVSwMzuTJXWZoVHbDdINioBwKy5kVmA==",
      "dependencies": {
        "@stablelib/constant-time": "^1.0.1",
        "@stablelib/hash": "^1.0.1",
        "@stablelib/wipe": "^1.0.1"
      }
    },
    "node_modules/@stablelib/int": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@stablelib/int/-/int-1.0.1.tgz",
      "integrity": "sha512-byr69X/sDtDiIjIV6m4roLVWnNNlRGzsvxw+agj8CIEazqWGOQp2dTYgQhtyVXV9wpO6WyXRQUzLV/JRNumT2w=="
    },
    "node_modules/@stablelib/keyagreement": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@stablelib/keyagreement/-/keyagreement-1.0.1.tgz",
      "integrity": "sha512-VKL6xBwgJnI6l1jKrBAfn265cspaWBPAPEc62VBQrWHLqVgNRE09gQ/AnOEyKUWrrqfD+xSQ3u42gJjLDdMDQg==",
      "dependencies": {
        "@stablelib/bytes": "^1.0.1"
      }
    },
    "node_modules/@stablelib/poly1305": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@stablelib/poly1305/-/poly1305-1.0.1.tgz",
      "integrity": "sha512-1HlG3oTSuQDOhSnLwJRKeTRSAdFNVB/1djy2ZbS35rBSJ/PFqx9cf9qatinWghC2UbfOYD8AcrtbUQl8WoxabA==",
      "dependencies": {
        "@stablelib/constant-time": "^1.0.1",
        "@stablelib/wipe": "^1.0.1"
      }
    },
    "node_modules/@stablelib/random": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/@stablelib/random/-/random-1.0.2.tgz",
      "integrity": "sha512-rIsE83Xpb7clHPVRlBj8qNe5L8ISQOzjghYQm/dZ7VaM2KHYwMW5adjQjrzTZCchFnNCNhkwtnOBa9HTMJCI8w==",
      "dependencies": {
        "@stablelib/binary": "^1.0.1",
        "@stablelib/wipe": "^1.0.1"
      }
    },
    "node_modules/@stablelib/sha256": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@stablelib/sha256/-/sha256-1.0.1.tgz",
      "integrity": "sha512-GIIH3e6KH+91FqGV42Kcj71Uefd/QEe7Dy42sBTeqppXV95ggCcxLTk39bEr+lZfJmp+ghsR07J++ORkRELsBQ==",
      "dependencies": {
        "@stablelib/binary": "^1.0.1",
        "@stablelib/hash": "^1.0.1",
        "@stablelib/wipe": "^1.0.1"
      }
    },
    "node_modules/@stablelib/sha512": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@stablelib/sha512/-/sha512-1.0.1.tgz",
      "integrity": "sha512-13gl/iawHV9zvDKciLo1fQ8Bgn2Pvf7OV6amaRVKiq3pjQ3UmEpXxWiAfV8tYjUpeZroBxtyrwtdooQT/i3hzw==",
      "dependencies": {
        "@stablelib/binary": "^1.0.1",
        "@stablelib/hash": "^1.0.1",
        "@stablelib/wipe": "^1.0.1"
      }
    },
    "node_modules/@stablelib/wipe": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@stablelib/wipe/-/wipe-1.0.1.tgz",
      "integrity": "sha512-WfqfX/eXGiAd3RJe4VU2snh/ZPwtSjLG4ynQ/vYzvghTh7dHFcI1wl+nrkWG6lGhukOxOsUHfv8dUXr58D0ayg=="
    },
    "node_modules/@stablelib/x25519": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/@stablelib/x25519/-/x25519-1.0.3.tgz",
      "integrity": "sha512-KnTbKmUhPhHavzobclVJQG5kuivH+qDLpe84iRqX3CLrKp881cF160JvXJ+hjn1aMyCwYOKeIZefIH/P5cJoRw==",
      "dependencies": {
        "@stablelib/keyagreement": "^1.0.1",
        "@stablelib/random": "^1.0.2",
        "@stablelib/wipe": "^1.0.1"
      }
    },
    "node_modules/@supabase/auth-js": {
      "version": "2.65.1",
      "resolved": "https://registry.npmjs.org/@supabase/auth-js/-/auth-js-2.65.1.tgz",
      "integrity": "sha512-IA7i2Xq2SWNCNMKxwmPlHafBQda0qtnFr8QnyyBr+KaSxoXXqEzFCnQ1dGTy6bsZjVBgXu++o3qrDypTspaAPw==",
      "dependencies": {
        "@supabase/node-fetch": "^2.6.14"
      }
    },
    "node_modules/@supabase/functions-js": {
      "version": "2.4.3",
      "resolved": "https://registry.npmjs.org/@supabase/functions-js/-/functions-js-2.4.3.tgz",
      "integrity": "sha512-sOLXy+mWRyu4LLv1onYydq+10mNRQ4rzqQxNhbrKLTLTcdcmS9hbWif0bGz/NavmiQfPs4ZcmQJp4WqOXlR4AQ==",
      "dependencies": {
        "@supabase/node-fetch": "^2.6.14"
      }
    },
    "node_modules/@supabase/node-fetch": {
      "version": "2.6.15",
      "resolved": "https://registry.npmjs.org/@supabase/node-fetch/-/node-fetch-2.6.15.tgz",
      "integrity": "sha512-1ibVeYUacxWYi9i0cf5efil6adJ9WRyZBLivgjs+AUpewx1F3xPi7gLgaASI2SmIQxPoCEjAsLAzKPgMJVgOUQ==",
      "dependencies": {
        "whatwg-url": "^5.0.0"
      },
      "engines": {
        "node": "4.x || >=6.0.0"
      }
    },
    "node_modules/@supabase/postgrest-js": {
      "version": "1.16.3",
      "resolved": "https://registry.npmjs.org/@supabase/postgrest-js/-/postgrest-js-1.16.3.tgz",
      "integrity": "sha512-HI6dsbW68AKlOPofUjDTaosiDBCtW4XAm0D18pPwxoW3zKOE2Ru13Z69Wuys9fd6iTpfDViNco5sgrtnP0666A==",
      "dependencies": {
        "@supabase/node-fetch": "^2.6.14"
      }
    },
    "node_modules/@supabase/realtime-js": {
      "version": "2.10.7",
      "resolved": "https://registry.npmjs.org/@supabase/realtime-js/-/realtime-js-2.10.7.tgz",
      "integrity": "sha512-OLI0hiSAqQSqRpGMTUwoIWo51eUivSYlaNBgxsXZE7PSoWh12wPRdVt0psUMaUzEonSB85K21wGc7W5jHnT6uA==",
      "dependencies": {
        "@supabase/node-fetch": "^2.6.14",
        "@types/phoenix": "^1.5.4",
        "@types/ws": "^8.5.10",
        "ws": "^8.14.2"
      }
    },
    "node_modules/@supabase/storage-js": {
      "version": "2.7.1",
      "resolved": "https://registry.npmjs.org/@supabase/storage-js/-/storage-js-2.7.1.tgz",
      "integrity": "sha512-asYHcyDR1fKqrMpytAS1zjyEfvxuOIp1CIXX7ji4lHHcJKqyk+sLl/Vxgm4sN6u8zvuUtae9e4kDxQP2qrwWBA==",
      "dependencies": {
        "@supabase/node-fetch": "^2.6.14"
      }
    },
    "node_modules/@supabase/supabase-js": {
      "version": "2.46.1",
      "resolved": "https://registry.npmjs.org/@supabase/supabase-js/-/supabase-js-2.46.1.tgz",
      "integrity": "sha512-HiBpd8stf7M6+tlr+/82L8b2QmCjAD8ex9YdSAKU+whB/SHXXJdus1dGlqiH9Umy9ePUuxaYmVkGd9BcvBnNvg==",
      "dependencies": {
        "@supabase/auth-js": "2.65.1",
        "@supabase/functions-js": "2.4.3",
        "@supabase/node-fetch": "2.6.15",
        "@supabase/postgrest-js": "1.16.3",
        "@supabase/realtime-js": "2.10.7",
        "@supabase/storage-js": "2.7.1"
      }
    },
    "node_modules/@swc/helpers": {
      "version": "0.5.13",
      "resolved": "https://registry.npmjs.org/@swc/helpers/-/helpers-0.5.13.tgz",
      "integrity": "sha512-UoKGxQ3r5kYI9dALKJapMmuK+1zWM/H17Z1+iwnNmzcJRnfFuevZs375TA5rW31pu4BS4NoSy1fRsexDXfWn5w==",
      "dependencies": {
        "tslib": "^2.4.0"
      }
    },
    "node_modules/@swc/helpers/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@tanem/svg-injector": {
      "version": "10.1.68",
      "resolved": "https://registry.npmjs.org/@tanem/svg-injector/-/svg-injector-10.1.68.tgz",
      "integrity": "sha512-UkJajeR44u73ujtr5GVSbIlELDWD/mzjqWe54YMK61ljKxFcJoPd9RBSaO7xj02ISCWUqJW99GjrS+sVF0UnrA==",
      "dependencies": {
        "@babel/runtime": "^7.23.2",
        "content-type": "^1.0.5",
        "tslib": "^2.6.2"
      }
    },
    "node_modules/@tanem/svg-injector/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/@types/babel__core": {
      "version": "7.20.5",
      "resolved": "https://registry.npmjs.org/@types/babel__core/-/babel__core-7.20.5.tgz",
      "integrity": "sha512-qoQprZvz5wQFJwMDqeseRXWv3rqMvhgpbXFfVyWhbx9X47POIA6i/+dXefEmZKoAgOaTdaIgNSMqMIU61yRyzA==",
      "dev": true,
      "dependencies": {
        "@babel/parser": "^7.20.7",
        "@babel/types": "^7.20.7",
        "@types/babel__generator": "*",
        "@types/babel__template": "*",
        "@types/babel__traverse": "*"
      }
    },
    "node_modules/@types/babel__generator": {
      "version": "7.6.8",
      "resolved": "https://registry.npmjs.org/@types/babel__generator/-/babel__generator-7.6.8.tgz",
      "integrity": "sha512-ASsj+tpEDsEiFr1arWrlN6V3mdfjRMZt6LtK/Vp/kreFLnr5QH5+DhvD5nINYZXzwJvXeGq+05iUXcAzVrqWtw==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.0.0"
      }
    },
    "node_modules/@types/babel__template": {
      "version": "7.4.4",
      "resolved": "https://registry.npmjs.org/@types/babel__template/-/babel__template-7.4.4.tgz",
      "integrity": "sha512-h/NUaSyG5EyxBIp8YRxo4RMe2/qQgvyowRwVMzhYhBCONbW8PUsg4lkFMrhgZhUe5z3L3MiLDuvyJ/CaPa2A8A==",
      "dev": true,
      "dependencies": {
        "@babel/parser": "^7.1.0",
        "@babel/types": "^7.0.0"
      }
    },
    "node_modules/@types/babel__traverse": {
      "version": "7.20.6",
      "resolved": "https://registry.npmjs.org/@types/babel__traverse/-/babel__traverse-7.20.6.tgz",
      "integrity": "sha512-r1bzfrm0tomOI8g1SzvCaQHo6Lcv6zu0EA+W2kHrt8dyrHQxGzBBL4kdkzIS+jBMV+EYcMAEAqXqYaLJq5rOZg==",
      "dev": true,
      "dependencies": {
        "@babel/types": "^7.20.7"
      }
    },
    "node_modules/@types/bn.js": {
      "version": "5.1.6",
      "resolved": "https://registry.npmjs.org/@types/bn.js/-/bn.js-5.1.6.tgz",
      "integrity": "sha512-Xh8vSwUeMKeYYrj3cX4lGQgFSF/N03r+tv4AiLl1SucqV+uTQpxRcnM8AkXKHwYP9ZPXOYXRr2KPXpVlIvqh9w==",
      "dependencies": {
        "@types/node": "*"
      }
    },
    "node_modules/@types/connect": {
      "version": "3.4.38",
      "resolved": "https://registry.npmjs.org/@types/connect/-/connect-3.4.38.tgz",
      "integrity": "sha512-K6uROf1LD88uDQqJCktA4yzL1YYAK6NgfsI0v/mTgyPKWsX1CnJ0XPSDhViejru1GcRkLWb8RlzFYJRqGUbaug==",
      "dependencies": {
        "@types/node": "*"
      }
    },
    "node_modules/@types/debug": {
      "version": "4.1.12",
      "resolved": "https://registry.npmjs.org/@types/debug/-/debug-4.1.12.tgz",
      "integrity": "sha512-vIChWdVG3LG1SMxEvI/AK+FWJthlrqlTu7fbrlywTkkaONwk/UAGaULXRlf8vkzFBLVm0zkMdCquhL5aOjhXPQ==",
      "dependencies": {
        "@types/ms": "*"
      }
    },
    "node_modules/@types/elliptic": {
      "version": "6.4.18",
      "resolved": "https://registry.npmjs.org/@types/elliptic/-/elliptic-6.4.18.tgz",
      "integrity": "sha512-UseG6H5vjRiNpQvrhy4VF/JXdA3V/Fp5amvveaL+fs28BZ6xIKJBPnUPRlEaZpysD9MbpfaLi8lbl7PGUAkpWw==",
      "dependencies": {
        "@types/bn.js": "*"
      }
    },
    "node_modules/@types/estree": {
      "version": "1.0.6",
      "resolved": "https://registry.npmjs.org/@types/estree/-/estree-1.0.6.tgz",
      "integrity": "sha512-AYnb1nQyY49te+VRAVgmzfcgjYS91mY5P0TKUDCLEM+gNnA+3T6rWITXRLYCpahpqSQbN5cE+gHpnPyXjHWxcw==",
      "dev": true
    },
    "node_modules/@types/json-schema": {
      "version": "7.0.15",
      "resolved": "https://registry.npmjs.org/@types/json-schema/-/json-schema-7.0.15.tgz",
      "integrity": "sha512-5+fP8P8MFNC+AyZCDxrB2pkZFPGzqQWUzpSeuuVLvm8VMcorNYavBqoFcxK8bQz4Qsbn4oUEEem4wDLfcysGHA==",
      "dev": true
    },
    "node_modules/@types/ms": {
      "version": "0.7.34",
      "resolved": "https://registry.npmjs.org/@types/ms/-/ms-0.7.34.tgz",
      "integrity": "sha512-nG96G3Wp6acyAgJqGasjODb+acrI7KltPiRxzHPXnP3NgI28bpQDRv53olbqGXbfcgF5aiiHmO3xpwEpS5Ld9g=="
    },
    "node_modules/@types/node": {
      "version": "22.8.6",
      "resolved": "https://registry.npmjs.org/@types/node/-/node-22.8.6.tgz",
      "integrity": "sha512-tosuJYKrIqjQIlVCM4PEGxOmyg3FCPa/fViuJChnGeEIhjA46oy8FMVoF9su1/v8PNs2a8Q0iFNyOx0uOF91nw==",
      "dependencies": {
        "undici-types": "~6.19.8"
      }
    },
    "node_modules/@types/phoenix": {
      "version": "1.6.5",
      "resolved": "https://registry.npmjs.org/@types/phoenix/-/phoenix-1.6.5.tgz",
      "integrity": "sha512-xegpDuR+z0UqG9fwHqNoy3rI7JDlvaPh2TY47Fl80oq6g+hXT+c/LEuE43X48clZ6lOfANl5WrPur9fYO1RJ/w=="
    },
    "node_modules/@types/prop-types": {
      "version": "15.7.13",
      "resolved": "https://registry.npmjs.org/@types/prop-types/-/prop-types-15.7.13.tgz",
      "integrity": "sha512-hCZTSvwbzWGvhqxp/RqVqwU999pBf2vp7hzIjiYOsl8wqOmUxkQ6ddw1cV3l8811+kdUFus/q4d1Y3E3SyEifA=="
    },
    "node_modules/@types/react": {
      "version": "18.3.12",
      "resolved": "https://registry.npmjs.org/@types/react/-/react-18.3.12.tgz",
      "integrity": "sha512-D2wOSq/d6Agt28q7rSI3jhU7G6aiuzljDGZ2hTZHIkrTLUI+AF3WMeKkEZ9nN2fkBAlcktT6vcZjDFiIhMYEQw==",
      "devOptional": true,
      "dependencies": {
        "@types/prop-types": "*",
        "csstype": "^3.0.2"
      }
    },
    "node_modules/@types/react-dom": {
      "version": "18.3.1",
      "resolved": "https://registry.npmjs.org/@types/react-dom/-/react-dom-18.3.1.tgz",
      "integrity": "sha512-qW1Mfv8taImTthu4KoXgDfLuk4bydU6Q/TkADnDWWHwi4NX4BR+LWfTp2sVmTqRrsHvyDDTelgelxJ+SsejKKQ==",
      "dev": true,
      "dependencies": {
        "@types/react": "*"
      }
    },
    "node_modules/@types/semver": {
      "version": "7.5.8",
      "resolved": "https://registry.npmjs.org/@types/semver/-/semver-7.5.8.tgz",
      "integrity": "sha512-I8EUhyrgfLrcTkzV3TSsGyl1tSuPrEDzr0yd5m90UgNxQkyDXULk3b6MlQqTCpZpNtWe1K0hzclnZkTcLBe2UQ==",
      "dev": true
    },
    "node_modules/@types/trusted-types": {
      "version": "2.0.7",
      "resolved": "https://registry.npmjs.org/@types/trusted-types/-/trusted-types-2.0.7.tgz",
      "integrity": "sha512-ScaPdn1dQczgbl0QFTeTOmVHFULt394XJgOQNoyVhZ6r2vLnMLJfBPd53SB52T/3G36VI1/g2MZaX0cwDuXsfw=="
    },
    "node_modules/@types/uuid": {
      "version": "8.3.4",
      "resolved": "https://registry.npmjs.org/@types/uuid/-/uuid-8.3.4.tgz",
      "integrity": "sha512-c/I8ZRb51j+pYGAu5CrFMRxqZ2ke4y2grEBO5AUjgSkSk+qT2Ea+OdWElz/OiMf5MNpn2b17kuVBwZLQJXzihw=="
    },
    "node_modules/@types/ws": {
      "version": "8.5.12",
      "resolved": "https://registry.npmjs.org/@types/ws/-/ws-8.5.12.tgz",
      "integrity": "sha512-3tPRkv1EtkDpzlgyKyI8pGsGZAGPEaXeu0DOj5DI25Ja91bdAYddYHbADRYVrZMRbfW+1l5YwXVDKohDJNQxkQ==",
      "dependencies": {
        "@types/node": "*"
      }
    },
    "node_modules/@typescript-eslint/eslint-plugin": {
      "version": "6.21.0",
      "resolved": "https://registry.npmjs.org/@typescript-eslint/eslint-plugin/-/eslint-plugin-6.21.0.tgz",
      "integrity": "sha512-oy9+hTPCUFpngkEZUSzbf9MxI65wbKFoQYsgPdILTfbUldp5ovUuphZVe4i30emU9M/kP+T64Di0mxl7dSw3MA==",
      "dev": true,
      "dependencies": {
        "@eslint-community/regexpp": "^4.5.1",
        "@typescript-eslint/scope-manager": "6.21.0",
        "@typescript-eslint/type-utils": "6.21.0",
        "@typescript-eslint/utils": "6.21.0",
        "@typescript-eslint/visitor-keys": "6.21.0",
        "debug": "^4.3.4",
        "graphemer": "^1.4.0",
        "ignore": "^5.2.4",
        "natural-compare": "^1.4.0",
        "semver": "^7.5.4",
        "ts-api-utils": "^1.0.1"
      },
      "engines": {
        "node": "^16.0.0 || >=18.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/typescript-eslint"
      },
      "peerDependencies": {
        "@typescript-eslint/parser": "^6.0.0 || ^6.0.0-alpha",
        "eslint": "^7.0.0 || ^8.0.0"
      },
      "peerDependenciesMeta": {
        "typescript": {
          "optional": true
        }
      }
    },
    "node_modules/@typescript-eslint/parser": {
      "version": "6.21.0",
      "resolved": "https://registry.npmjs.org/@typescript-eslint/parser/-/parser-6.21.0.tgz",
      "integrity": "sha512-tbsV1jPne5CkFQCgPBcDOt30ItF7aJoZL997JSF7MhGQqOeT3svWRYxiqlfA5RUdlHN6Fi+EI9bxqbdyAUZjYQ==",
      "dev": true,
      "dependencies": {
        "@typescript-eslint/scope-manager": "6.21.0",
        "@typescript-eslint/types": "6.21.0",
        "@typescript-eslint/typescript-estree": "6.21.0",
        "@typescript-eslint/visitor-keys": "6.21.0",
        "debug": "^4.3.4"
      },
      "engines": {
        "node": "^16.0.0 || >=18.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/typescript-eslint"
      },
      "peerDependencies": {
        "eslint": "^7.0.0 || ^8.0.0"
      },
      "peerDependenciesMeta": {
        "typescript": {
          "optional": true
        }
      }
    },
    "node_modules/@typescript-eslint/scope-manager": {
      "version": "6.21.0",
      "resolved": "https://registry.npmjs.org/@typescript-eslint/scope-manager/-/scope-manager-6.21.0.tgz",
      "integrity": "sha512-OwLUIWZJry80O99zvqXVEioyniJMa+d2GrqpUTqi5/v5D5rOrppJVBPa0yKCblcigC0/aYAzxxqQ1B+DS2RYsg==",
      "dev": true,
      "dependencies": {
        "@typescript-eslint/types": "6.21.0",
        "@typescript-eslint/visitor-keys": "6.21.0"
      },
      "engines": {
        "node": "^16.0.0 || >=18.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/typescript-eslint"
      }
    },
    "node_modules/@typescript-eslint/type-utils": {
      "version": "6.21.0",
      "resolved": "https://registry.npmjs.org/@typescript-eslint/type-utils/-/type-utils-6.21.0.tgz",
      "integrity": "sha512-rZQI7wHfao8qMX3Rd3xqeYSMCL3SoiSQLBATSiVKARdFGCYSRvmViieZjqc58jKgs8Y8i9YvVVhRbHSTA4VBag==",
      "dev": true,
      "dependencies": {
        "@typescript-eslint/typescript-estree": "6.21.0",
        "@typescript-eslint/utils": "6.21.0",
        "debug": "^4.3.4",
        "ts-api-utils": "^1.0.1"
      },
      "engines": {
        "node": "^16.0.0 || >=18.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/typescript-eslint"
      },
      "peerDependencies": {
        "eslint": "^7.0.0 || ^8.0.0"
      },
      "peerDependenciesMeta": {
        "typescript": {
          "optional": true
        }
      }
    },
    "node_modules/@typescript-eslint/types": {
      "version": "6.21.0",
      "resolved": "https://registry.npmjs.org/@typescript-eslint/types/-/types-6.21.0.tgz",
      "integrity": "sha512-1kFmZ1rOm5epu9NZEZm1kckCDGj5UJEf7P1kliH4LKu/RkwpsfqqGmY2OOcUs18lSlQBKLDYBOGxRVtrMN5lpg==",
      "dev": true,
      "engines": {
        "node": "^16.0.0 || >=18.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/typescript-eslint"
      }
    },
    "node_modules/@typescript-eslint/typescript-estree": {
      "version": "6.21.0",
      "resolved": "https://registry.npmjs.org/@typescript-eslint/typescript-estree/-/typescript-estree-6.21.0.tgz",
      "integrity": "sha512-6npJTkZcO+y2/kr+z0hc4HwNfrrP4kNYh57ek7yCNlrBjWQ1Y0OS7jiZTkgumrvkX5HkEKXFZkkdFNkaW2wmUQ==",
      "dev": true,
      "dependencies": {
        "@typescript-eslint/types": "6.21.0",
        "@typescript-eslint/visitor-keys": "6.21.0",
        "debug": "^4.3.4",
        "globby": "^11.1.0",
        "is-glob": "^4.0.3",
        "minimatch": "9.0.3",
        "semver": "^7.5.4",
        "ts-api-utils": "^1.0.1"
      },
      "engines": {
        "node": "^16.0.0 || >=18.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/typescript-eslint"
      },
      "peerDependenciesMeta": {
        "typescript": {
          "optional": true
        }
      }
    },
    "node_modules/@typescript-eslint/utils": {
      "version": "6.21.0",
      "resolved": "https://registry.npmjs.org/@typescript-eslint/utils/-/utils-6.21.0.tgz",
      "integrity": "sha512-NfWVaC8HP9T8cbKQxHcsJBY5YE1O33+jpMwN45qzWWaPDZgLIbo12toGMWnmhvCpd3sIxkpDw3Wv1B3dYrbDQQ==",
      "dev": true,
      "dependencies": {
        "@eslint-community/eslint-utils": "^4.4.0",
        "@types/json-schema": "^7.0.12",
        "@types/semver": "^7.5.0",
        "@typescript-eslint/scope-manager": "6.21.0",
        "@typescript-eslint/types": "6.21.0",
        "@typescript-eslint/typescript-estree": "6.21.0",
        "semver": "^7.5.4"
      },
      "engines": {
        "node": "^16.0.0 || >=18.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/typescript-eslint"
      },
      "peerDependencies": {
        "eslint": "^7.0.0 || ^8.0.0"
      }
    },
    "node_modules/@typescript-eslint/visitor-keys": {
      "version": "6.21.0",
      "resolved": "https://registry.npmjs.org/@typescript-eslint/visitor-keys/-/visitor-keys-6.21.0.tgz",
      "integrity": "sha512-JJtkDduxLi9bivAB+cYOVMtbkqdPOhZ+ZI5LC47MIRrDV4Yn2o+ZnW10Nkmr28xRpSpdJ6Sm42Hjf2+REYXm0A==",
      "dev": true,
      "dependencies": {
        "@typescript-eslint/types": "6.21.0",
        "eslint-visitor-keys": "^3.4.1"
      },
      "engines": {
        "node": "^16.0.0 || >=18.0.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/typescript-eslint"
      }
    },
    "node_modules/@ungap/structured-clone": {
      "version": "1.2.0",
      "resolved": "https://registry.npmjs.org/@ungap/structured-clone/-/structured-clone-1.2.0.tgz",
      "integrity": "sha512-zuVdFrMJiuCDQUMCzQaD6KL28MjnqqN8XnAqiEq9PNm/hCPTSGfrXCOfwj1ow4LFb/tNymJPwsNbVePc1xFqrQ==",
      "dev": true
    },
    "node_modules/@vitejs/plugin-react": {
      "version": "4.3.3",
      "resolved": "https://registry.npmjs.org/@vitejs/plugin-react/-/plugin-react-4.3.3.tgz",
      "integrity": "sha512-NooDe9GpHGqNns1i8XDERg0Vsg5SSYRhRxxyTGogUdkdNt47jal+fbuYi+Yfq6pzRCKXyoPcWisfxE6RIM3GKA==",
      "dev": true,
      "dependencies": {
        "@babel/core": "^7.25.2",
        "@babel/plugin-transform-react-jsx-self": "^7.24.7",
        "@babel/plugin-transform-react-jsx-source": "^7.24.7",
        "@types/babel__core": "^7.20.5",
        "react-refresh": "^0.14.2"
      },
      "engines": {
        "node": "^14.18.0 || >=16.0.0"
      },
      "peerDependencies": {
        "vite": "^4.2.0 || ^5.0.0"
      }
    },
    "node_modules/@walletconnect/environment": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@walletconnect/environment/-/environment-1.0.1.tgz",
      "integrity": "sha512-T426LLZtHj8e8rYnKfzsw1aG6+M0BT1ZxayMdv/p8yM0MU+eJDISqNY3/bccxRr4LrF9csq02Rhqt08Ibl0VRg==",
      "dependencies": {
        "tslib": "1.14.1"
      }
    },
    "node_modules/@walletconnect/events": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@walletconnect/events/-/events-1.0.1.tgz",
      "integrity": "sha512-NPTqaoi0oPBVNuLv7qPaJazmGHs5JGyO8eEAk5VGKmJzDR7AHzD4k6ilox5kxk1iwiOnFopBOOMLs86Oa76HpQ==",
      "dependencies": {
        "keyvaluestorage-interface": "^1.0.0",
        "tslib": "1.14.1"
      }
    },
    "node_modules/@walletconnect/heartbeat": {
      "version": "1.2.1",
      "resolved": "https://registry.npmjs.org/@walletconnect/heartbeat/-/heartbeat-1.2.1.tgz",
      "integrity": "sha512-yVzws616xsDLJxuG/28FqtZ5rzrTA4gUjdEMTbWB5Y8V1XHRmqq4efAxCw5ie7WjbXFSUyBHaWlMR+2/CpQC5Q==",
      "dependencies": {
        "@walletconnect/events": "^1.0.1",
        "@walletconnect/time": "^1.0.2",
        "tslib": "1.14.1"
      }
    },
    "node_modules/@walletconnect/jsonrpc-http-connection": {
      "version": "1.0.8",
      "resolved": "https://registry.npmjs.org/@walletconnect/jsonrpc-http-connection/-/jsonrpc-http-connection-1.0.8.tgz",
      "integrity": "sha512-+B7cRuaxijLeFDJUq5hAzNyef3e3tBDIxyaCNmFtjwnod5AGis3RToNqzFU33vpVcxFhofkpE7Cx+5MYejbMGw==",
      "dependencies": {
        "@walletconnect/jsonrpc-utils": "^1.0.6",
        "@walletconnect/safe-json": "^1.0.1",
        "cross-fetch": "^3.1.4",
        "events": "^3.3.0"
      }
    },
    "node_modules/@walletconnect/jsonrpc-types": {
      "version": "1.0.4",
      "resolved": "https://registry.npmjs.org/@walletconnect/jsonrpc-types/-/jsonrpc-types-1.0.4.tgz",
      "integrity": "sha512-P6679fG/M+wuWg9TY8mh6xFSdYnFyFjwFelxyISxMDrlbXokorEVXYOxiqEbrU3x1BmBoCAJJ+vtEaEoMlpCBQ==",
      "dependencies": {
        "events": "^3.3.0",
        "keyvaluestorage-interface": "^1.0.0"
      }
    },
    "node_modules/@walletconnect/jsonrpc-utils": {
      "version": "1.0.8",
      "resolved": "https://registry.npmjs.org/@walletconnect/jsonrpc-utils/-/jsonrpc-utils-1.0.8.tgz",
      "integrity": "sha512-vdeb03bD8VzJUL6ZtzRYsFMq1eZQcM3EAzT0a3st59dyLfJ0wq+tKMpmGH7HlB7waD858UWgfIcudbPFsbzVdw==",
      "dependencies": {
        "@walletconnect/environment": "^1.0.1",
        "@walletconnect/jsonrpc-types": "^1.0.3",
        "tslib": "1.14.1"
      }
    },
    "node_modules/@walletconnect/keyvaluestorage": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/@walletconnect/keyvaluestorage/-/keyvaluestorage-1.1.1.tgz",
      "integrity": "sha512-V7ZQq2+mSxAq7MrRqDxanTzu2RcElfK1PfNYiaVnJgJ7Q7G7hTVwF8voIBx92qsRyGHZihrwNPHuZd1aKkd0rA==",
      "dependencies": {
        "@walletconnect/safe-json": "^1.0.1",
        "idb-keyval": "^6.2.1",
        "unstorage": "^1.9.0"
      },
      "peerDependencies": {
        "@react-native-async-storage/async-storage": "1.x"
      },
      "peerDependenciesMeta": {
        "@react-native-async-storage/async-storage": {
          "optional": true
        }
      }
    },
    "node_modules/@walletconnect/logger": {
      "version": "2.1.2",
      "resolved": "https://registry.npmjs.org/@walletconnect/logger/-/logger-2.1.2.tgz",
      "integrity": "sha512-aAb28I3S6pYXZHQm5ESB+V6rDqIYfsnHaQyzFbwUUBFY4H0OXx/YtTl8lvhUNhMMfb9UxbwEBS253TlXUYJWSw==",
      "dependencies": {
        "@walletconnect/safe-json": "^1.0.2",
        "pino": "7.11.0"
      }
    },
    "node_modules/@walletconnect/modal": {
      "version": "2.6.2",
      "resolved": "https://registry.npmjs.org/@walletconnect/modal/-/modal-2.6.2.tgz",
      "integrity": "sha512-eFopgKi8AjKf/0U4SemvcYw9zlLpx9njVN8sf6DAkowC2Md0gPU/UNEbH1Wwj407pEKnEds98pKWib1NN1ACoA==",
      "dependencies": {
        "@walletconnect/modal-core": "2.6.2",
        "@walletconnect/modal-ui": "2.6.2"
      }
    },
    "node_modules/@walletconnect/modal-core": {
      "version": "2.6.2",
      "resolved": "https://registry.npmjs.org/@walletconnect/modal-core/-/modal-core-2.6.2.tgz",
      "integrity": "sha512-cv8ibvdOJQv2B+nyxP9IIFdxvQznMz8OOr/oR/AaUZym4hjXNL/l1a2UlSQBXrVjo3xxbouMxLb3kBsHoYP2CA==",
      "dependencies": {
        "valtio": "1.11.2"
      }
    },
    "node_modules/@walletconnect/modal-ui": {
      "version": "2.6.2",
      "resolved": "https://registry.npmjs.org/@walletconnect/modal-ui/-/modal-ui-2.6.2.tgz",
      "integrity": "sha512-rbdstM1HPGvr7jprQkyPggX7rP4XiCG85ZA+zWBEX0dVQg8PpAgRUqpeub4xQKDgY7pY/xLRXSiCVdWGqvG2HA==",
      "dependencies": {
        "@walletconnect/modal-core": "2.6.2",
        "lit": "2.8.0",
        "motion": "10.16.2",
        "qrcode": "1.5.3"
      }
    },
    "node_modules/@walletconnect/modal-ui/node_modules/qrcode": {
      "version": "1.5.3",
      "resolved": "https://registry.npmjs.org/qrcode/-/qrcode-1.5.3.tgz",
      "integrity": "sha512-puyri6ApkEHYiVl4CFzo1tDkAZ+ATcnbJrJ6RiBM1Fhctdn/ix9MTE3hRph33omisEbC/2fcfemsseiKgBPKZg==",
      "dependencies": {
        "dijkstrajs": "^1.0.1",
        "encode-utf8": "^1.0.3",
        "pngjs": "^5.0.0",
        "yargs": "^15.3.1"
      },
      "bin": {
        "qrcode": "bin/qrcode"
      },
      "engines": {
        "node": ">=10.13.0"
      }
    },
    "node_modules/@walletconnect/relay-api": {
      "version": "1.0.11",
      "resolved": "https://registry.npmjs.org/@walletconnect/relay-api/-/relay-api-1.0.11.tgz",
      "integrity": "sha512-tLPErkze/HmC9aCmdZOhtVmYZq1wKfWTJtygQHoWtgg722Jd4homo54Cs4ak2RUFUZIGO2RsOpIcWipaua5D5Q==",
      "dependencies": {
        "@walletconnect/jsonrpc-types": "^1.0.2"
      }
    },
    "node_modules/@walletconnect/relay-auth": {
      "version": "1.0.4",
      "resolved": "https://registry.npmjs.org/@walletconnect/relay-auth/-/relay-auth-1.0.4.tgz",
      "integrity": "sha512-kKJcS6+WxYq5kshpPaxGHdwf5y98ZwbfuS4EE/NkQzqrDFm5Cj+dP8LofzWvjrrLkZq7Afy7WrQMXdLy8Sx7HQ==",
      "dependencies": {
        "@stablelib/ed25519": "^1.0.2",
        "@stablelib/random": "^1.0.1",
        "@walletconnect/safe-json": "^1.0.1",
        "@walletconnect/time": "^1.0.2",
        "tslib": "1.14.1",
        "uint8arrays": "^3.0.0"
      }
    },
    "node_modules/@walletconnect/safe-json": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/@walletconnect/safe-json/-/safe-json-1.0.2.tgz",
      "integrity": "sha512-Ogb7I27kZ3LPC3ibn8ldyUr5544t3/STow9+lzz7Sfo808YD7SBWk7SAsdBFlYgP2zDRy2hS3sKRcuSRM0OTmA==",
      "dependencies": {
        "tslib": "1.14.1"
      }
    },
    "node_modules/@walletconnect/time": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/@walletconnect/time/-/time-1.0.2.tgz",
      "integrity": "sha512-uzdd9woDcJ1AaBZRhqy5rNC9laqWGErfc4dxA9a87mPdKOgWMD85mcFo9dIYIts/Jwocfwn07EC6EzclKubk/g==",
      "dependencies": {
        "tslib": "1.14.1"
      }
    },
    "node_modules/@walletconnect/window-getters": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@walletconnect/window-getters/-/window-getters-1.0.1.tgz",
      "integrity": "sha512-vHp+HqzGxORPAN8gY03qnbTMnhqIwjeRJNOMOAzePRg4xVEEE2WvYsI9G2NMjOknA8hnuYbU3/hwLcKbjhc8+Q==",
      "dependencies": {
        "tslib": "1.14.1"
      }
    },
    "node_modules/@walletconnect/window-metadata": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/@walletconnect/window-metadata/-/window-metadata-1.0.1.tgz",
      "integrity": "sha512-9koTqyGrM2cqFRW517BPY/iEtUDx2r1+Pwwu5m7sJ7ka79wi3EyqhqcICk/yDmv6jAS1rjKgTKXlEhanYjijcA==",
      "dependencies": {
        "@walletconnect/window-getters": "^1.0.1",
        "tslib": "1.14.1"
      }
    },
    "node_modules/abitype": {
      "version": "1.0.6",
      "resolved": "https://registry.npmjs.org/abitype/-/abitype-1.0.6.tgz",
      "integrity": "sha512-MMSqYh4+C/aVqI2RQaWqbvI4Kxo5cQV40WQ4QFtDnNzCkqChm8MuENhElmynZlO0qUy/ObkEUaXtKqYnx1Kp3A==",
      "funding": {
        "url": "https://github.com/sponsors/wevm"
      },
      "peerDependencies": {
        "typescript": ">=5.0.4",
        "zod": "^3 >=3.22.0"
      },
      "peerDependenciesMeta": {
        "typescript": {
          "optional": true
        },
        "zod": {
          "optional": true
        }
      }
    },
    "node_modules/abort-controller": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/abort-controller/-/abort-controller-3.0.0.tgz",
      "integrity": "sha512-h8lQ8tacZYnR3vNQTgibj+tODHI5/+l06Au2Pcriv/Gmet0eaj4TwWH41sO9wnHDiQsEj19q0drzdWdeAHtweg==",
      "dependencies": {
        "event-target-shim": "^5.0.0"
      },
      "engines": {
        "node": ">=6.5"
      }
    },
    "node_modules/acorn": {
      "version": "8.14.0",
      "resolved": "https://registry.npmjs.org/acorn/-/acorn-8.14.0.tgz",
      "integrity": "sha512-cl669nCJTZBsL97OF4kUQm5g5hC2uihk0NxY3WENAC0TYdILVkAyHymAntgxGkl7K+t0cXIrH5siy5S4XkFycA==",
      "bin": {
        "acorn": "bin/acorn"
      },
      "engines": {
        "node": ">=0.4.0"
      }
    },
    "node_modules/acorn-jsx": {
      "version": "5.3.2",
      "resolved": "https://registry.npmjs.org/acorn-jsx/-/acorn-jsx-5.3.2.tgz",
      "integrity": "sha512-rq9s+JNhf0IChjtDXxllJ7g41oZk5SlXtp0LHwyA5cejwn7vKmKp4pPri6YEePv2PU65sAsegbXtIinmDFDXgQ==",
      "dev": true,
      "peerDependencies": {
        "acorn": "^6.0.0 || ^7.0.0 || ^8.0.0"
      }
    },
    "node_modules/agentkeepalive": {
      "version": "4.5.0",
      "resolved": "https://registry.npmjs.org/agentkeepalive/-/agentkeepalive-4.5.0.tgz",
      "integrity": "sha512-5GG/5IbQQpC9FpkRGsSvZI5QYeSCzlJHdpBQntCsuTOxhKD8lqKhrleg2Yi7yvMIf82Ycmmqln9U8V9qwEiJew==",
      "dependencies": {
        "humanize-ms": "^1.2.1"
      },
      "engines": {
        "node": ">= 8.0.0"
      }
    },
    "node_modules/ahooks": {
      "version": "3.8.1",
      "resolved": "https://registry.npmjs.org/ahooks/-/ahooks-3.8.1.tgz",
      "integrity": "sha512-JoP9+/RWO7MnI/uSKdvQ8WB10Y3oo1PjLv+4Sv4Vpm19Z86VUMdXh+RhWvMGxZZs06sq2p0xVtFk8Oh5ZObsoA==",
      "dependencies": {
        "@babel/runtime": "^7.21.0",
        "dayjs": "^1.9.1",
        "intersection-observer": "^0.12.0",
        "js-cookie": "^3.0.5",
        "lodash": "^4.17.21",
        "react-fast-compare": "^3.2.2",
        "resize-observer-polyfill": "^1.5.1",
        "screenfull": "^5.0.0",
        "tslib": "^2.4.1"
      },
      "engines": {
        "node": ">=8.0.0"
      },
      "peerDependencies": {
        "react": "^16.8.0 || ^17.0.0 || ^18.0.0"
      }
    },
    "node_modules/ahooks/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/ajv": {
      "version": "6.12.6",
      "resolved": "https://registry.npmjs.org/ajv/-/ajv-6.12.6.tgz",
      "integrity": "sha512-j3fVLgvTo527anyYyJOGTYJbG+vnnQYvE0m5mmkc1TK+nxAppkCLMIL0aZ4dblVCNoGShhm+kzE4ZUykBoMg4g==",
      "dev": true,
      "dependencies": {
        "fast-deep-equal": "^3.1.1",
        "fast-json-stable-stringify": "^2.0.0",
        "json-schema-traverse": "^0.4.1",
        "uri-js": "^4.2.2"
      },
      "funding": {
        "type": "github",
        "url": "https://github.com/sponsors/epoberezkin"
      }
    },
    "node_modules/ansi-regex": {
      "version": "5.0.1",
      "resolved": "https://registry.npmjs.org/ansi-regex/-/ansi-regex-5.0.1.tgz",
      "integrity": "sha512-quJQXlTSUGL2LH9SUXo8VwsY4soanhgo6LNSm84E1LBcE8s3O0wpdiRzyR9z/ZZJMlMWv37qOOb9pdJlMUEKFQ==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/ansi-styles": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/ansi-styles/-/ansi-styles-4.3.0.tgz",
      "integrity": "sha512-zbB9rCJAT1rbjiVDb2hqKFHNYLxgtk8NURxZ3IZwD3F6NtxbXZQCnnSi1Lkx+IDohdPlFp222wVALIheZJQSEg==",
      "dependencies": {
        "color-convert": "^2.0.1"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/chalk/ansi-styles?sponsor=1"
      }
    },
    "node_modules/antd": {
      "version": "4.24.16",
      "resolved": "https://registry.npmjs.org/antd/-/antd-4.24.16.tgz",
      "integrity": "sha512-zZrK4UYxHtU6tGOOf0uG/kBRx1kTvypfuSB3GqE/SBQxFhZ/TZ+yj7Z1qwI8vGfMtUUJdLeuoCAqGDa1zPsXnQ==",
      "dependencies": {
        "@ant-design/colors": "^6.0.0",
        "@ant-design/icons": "^4.8.2",
        "@ant-design/react-slick": "~1.0.2",
        "@babel/runtime": "^7.18.3",
        "@ctrl/tinycolor": "^3.6.1",
        "classnames": "^2.2.6",
        "copy-to-clipboard": "^3.2.0",
        "lodash": "^4.17.21",
        "moment": "^2.29.2",
        "rc-cascader": "~3.7.3",
        "rc-checkbox": "~3.0.1",
        "rc-collapse": "~3.4.2",
        "rc-dialog": "~9.0.2",
        "rc-drawer": "~6.3.0",
        "rc-dropdown": "~4.0.1",
        "rc-field-form": "~1.38.2",
        "rc-image": "~5.13.0",
        "rc-input": "~0.1.4",
        "rc-input-number": "~7.3.11",
        "rc-mentions": "~1.13.1",
        "rc-menu": "~9.8.4",
        "rc-motion": "^2.9.0",
        "rc-notification": "~4.6.1",
        "rc-pagination": "~3.2.0",
        "rc-picker": "~2.7.6",
        "rc-progress": "~3.4.2",
        "rc-rate": "~2.9.3",
        "rc-resize-observer": "^1.3.1",
        "rc-segmented": "~2.3.0",
        "rc-select": "~14.1.18",
        "rc-slider": "~10.0.1",
        "rc-steps": "~5.0.0",
        "rc-switch": "~3.2.2",
        "rc-table": "~7.26.0",
        "rc-tabs": "~12.5.10",
        "rc-textarea": "~0.4.7",
        "rc-tooltip": "~5.2.2",
        "rc-tree": "~5.7.12",
        "rc-tree-select": "~5.5.5",
        "rc-trigger": "^5.3.4",
        "rc-upload": "~4.3.6",
        "rc-util": "^5.37.0",
        "scroll-into-view-if-needed": "^2.2.25"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/ant-design"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/any-promise": {
      "version": "1.3.0",
      "resolved": "https://registry.npmjs.org/any-promise/-/any-promise-1.3.0.tgz",
      "integrity": "sha512-7UvmKalWRt1wgjL1RrGxoSJW/0QZFIegpeGvZG9kjp8vrRu55XTHbwnqq2GpXm9uLbcuhxm3IqX9OB4MZR1b2A==",
      "dev": true
    },
    "node_modules/anymatch": {
      "version": "3.1.3",
      "resolved": "https://registry.npmjs.org/anymatch/-/anymatch-3.1.3.tgz",
      "integrity": "sha512-KMReFUr0B4t+D+OBkjR3KYqvocp2XaSzO55UcB6mgQMd3KbcE+mWTyvVV7D/zsdEbNnV6acZUutkiHQXvTr1Rw==",
      "dependencies": {
        "normalize-path": "^3.0.0",
        "picomatch": "^2.0.4"
      },
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/arch": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/arch/-/arch-2.2.0.tgz",
      "integrity": "sha512-Of/R0wqp83cgHozfIYLbBMnej79U/SVGOOyuB3VVFv1NRM/PSFMK12x9KVtiYzJqmnU5WR2qp0Z5rHb7sWGnFQ==",
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/feross"
        },
        {
          "type": "patreon",
          "url": "https://www.patreon.com/feross"
        },
        {
          "type": "consulting",
          "url": "https://feross.org/support"
        }
      ]
    },
    "node_modules/arg": {
      "version": "5.0.2",
      "resolved": "https://registry.npmjs.org/arg/-/arg-5.0.2.tgz",
      "integrity": "sha512-PYjyFOLKQ9y57JvQ6QLo8dAgNqswh8M1RMJYdQduT6xbWSgK36P/Z/v+p888pM69jMMfS8Xd8F6I1kQ/I9HUGg=="
    },
    "node_modules/argparse": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/argparse/-/argparse-2.0.1.tgz",
      "integrity": "sha512-8+9WqebbFzpX9OR+Wa6O29asIogeRMzcGtAINdpMHHyAg10f05aSFVBbcEqGf/PXw1EjAZ+q2/bEBg3DvurK3Q==",
      "dev": true
    },
    "node_modules/array-tree-filter": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/array-tree-filter/-/array-tree-filter-2.1.0.tgz",
      "integrity": "sha512-4ROwICNlNw/Hqa9v+rk5h22KjmzB1JGTMVKP2AKJBOCgb0yL0ASf0+YvCcLNNwquOHNX48jkeZIJ3a+oOQqKcw=="
    },
    "node_modules/array-union": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/array-union/-/array-union-2.1.0.tgz",
      "integrity": "sha512-HGyxoOTYUyCM6stUe6EJgnd4EoewAI7zMdfqO+kGjnlZmBDz/cR5pf8r/cR4Wq60sL/p0IkcjUEEPwS3GFrIyw==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/async-mutex": {
      "version": "0.2.6",
      "resolved": "https://registry.npmjs.org/async-mutex/-/async-mutex-0.2.6.tgz",
      "integrity": "sha512-Hs4R+4SPgamu6rSGW8C7cV9gaWUKEHykfzCCvIRuaVv636Ju10ZdeUbvb4TBEW0INuq2DHZqXbK4Nd3yG4RaRw==",
      "dependencies": {
        "tslib": "^2.0.0"
      }
    },
    "node_modules/async-mutex/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/async-validator": {
      "version": "4.2.5",
      "resolved": "https://registry.npmjs.org/async-validator/-/async-validator-4.2.5.tgz",
      "integrity": "sha512-7HhHjtERjqlNbZtqNqy2rckN/SpOOlmDliet+lP7k+eKZEjPk3DgyeU9lIXLdeLz0uBbbVp+9Qdow9wJWgwwfg=="
    },
    "node_modules/asynckit": {
      "version": "0.4.0",
      "resolved": "https://registry.npmjs.org/asynckit/-/asynckit-0.4.0.tgz",
      "integrity": "sha512-Oei9OH4tRh0YqU3GxhX79dM/mwVgvbZJaSNaRk+bshkj0S5cfHcgYakreBjrHwatXKbz+IoIdYLxrKim2MjW0Q=="
    },
    "node_modules/atomic-sleep": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/atomic-sleep/-/atomic-sleep-1.0.0.tgz",
      "integrity": "sha512-kNOjDqAh7px0XWNI+4QbzoiR/nTkHAWNud2uvnJquD1/x5a7EQZMJT0AczqK0Qn67oY/TTQ1LbUKajZpp3I9tQ==",
      "engines": {
        "node": ">=8.0.0"
      }
    },
    "node_modules/autoprefixer": {
      "version": "10.4.20",
      "resolved": "https://registry.npmjs.org/autoprefixer/-/autoprefixer-10.4.20.tgz",
      "integrity": "sha512-XY25y5xSv/wEoqzDyXXME4AFfkZI0P23z6Fs3YgymDnKJkCGOnkL0iTxCa85UTqaSgfcqyf3UA6+c7wUvx/16g==",
      "dev": true,
      "funding": [
        {
          "type": "opencollective",
          "url": "https://opencollective.com/postcss/"
        },
        {
          "type": "tidelift",
          "url": "https://tidelift.com/funding/github/npm/autoprefixer"
        },
        {
          "type": "github",
          "url": "https://github.com/sponsors/ai"
        }
      ],
      "dependencies": {
        "browserslist": "^4.23.3",
        "caniuse-lite": "^1.0.30001646",
        "fraction.js": "^4.3.7",
        "normalize-range": "^0.1.2",
        "picocolors": "^1.0.1",
        "postcss-value-parser": "^4.2.0"
      },
      "bin": {
        "autoprefixer": "bin/autoprefixer"
      },
      "engines": {
        "node": "^10 || ^12 || >=14"
      },
      "peerDependencies": {
        "postcss": "^8.1.0"
      }
    },
    "node_modules/axios": {
      "version": "1.7.7",
      "resolved": "https://registry.npmjs.org/axios/-/axios-1.7.7.tgz",
      "integrity": "sha512-S4kL7XrjgBmvdGut0sN3yJxqYzrDOnivkBiN0OFs6hLiUam3UPvswUo0kqGyhqUZGEOytHyumEdXsAkgCOUf3Q==",
      "dependencies": {
        "follow-redirects": "^1.15.6",
        "form-data": "^4.0.0",
        "proxy-from-env": "^1.1.0"
      }
    },
    "node_modules/balanced-match": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/balanced-match/-/balanced-match-1.0.2.tgz",
      "integrity": "sha512-3oSeUO0TMV67hN1AmbXsK4yaqU7tjiHlbxRDZOpH0KW9+CeX4bRAaX0Anxt0tx2MrpRpWwQaPwIlISEJhYU5Pw==",
      "dev": true
    },
    "node_modules/base-x": {
      "version": "3.0.10",
      "resolved": "https://registry.npmjs.org/base-x/-/base-x-3.0.10.tgz",
      "integrity": "sha512-7d0s06rR9rYaIWHkpfLIFICM/tkSVdoPC9qYAQRpxn9DdKNWNsKC0uk++akckyLq16Tx2WIinnZ6WRriAt6njQ==",
      "dependencies": {
        "safe-buffer": "^5.0.1"
      }
    },
    "node_modules/base64-js": {
      "version": "1.5.1",
      "resolved": "https://registry.npmjs.org/base64-js/-/base64-js-1.5.1.tgz",
      "integrity": "sha512-AKpaYlHn8t4SVbOHCy+b5+KKgvR4vrsD8vbvrbiQJps7fKDTkjkDry6ji0rUJjC0kzbNePLwzxq8iypo41qeWA==",
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/feross"
        },
        {
          "type": "patreon",
          "url": "https://www.patreon.com/feross"
        },
        {
          "type": "consulting",
          "url": "https://feross.org/support"
        }
      ]
    },
    "node_modules/base64url": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/base64url/-/base64url-3.0.1.tgz",
      "integrity": "sha512-ir1UPr3dkwexU7FdV8qBBbNDRUhMmIekYMFZfi+C/sLNnRESKPl23nB9b2pltqfOQNnGzsDdId90AEtG5tCx4A==",
      "engines": {
        "node": ">=6.0.0"
      }
    },
    "node_modules/bigint-buffer": {
      "version": "1.1.5",
      "resolved": "https://registry.npmjs.org/bigint-buffer/-/bigint-buffer-1.1.5.tgz",
      "integrity": "sha512-trfYco6AoZ+rKhKnxA0hgX0HAbVP/s808/EuDSe2JDzUnCp/xAsli35Orvk67UrTEcwuxZqYZDmfA2RXJgxVvA==",
      "hasInstallScript": true,
      "dependencies": {
        "bindings": "^1.3.0"
      },
      "engines": {
        "node": ">= 10.0.0"
      }
    },
    "node_modules/bignumber.js": {
      "version": "9.1.2",
      "resolved": "https://registry.npmjs.org/bignumber.js/-/bignumber.js-9.1.2.tgz",
      "integrity": "sha512-2/mKyZH9K85bzOEfhXDBFZTGd1CTs+5IHpeFQo9luiBG7hghdC851Pj2WAhb6E3R6b9tZj/XKhbg4fum+Kepug==",
      "engines": {
        "node": "*"
      }
    },
    "node_modules/binary-extensions": {
      "version": "2.3.0",
      "resolved": "https://registry.npmjs.org/binary-extensions/-/binary-extensions-2.3.0.tgz",
      "integrity": "sha512-Ceh+7ox5qe7LJuLHoY0feh3pHuUDHAcRUeyL2VYghZwfpkNIy/+8Ocg0a3UuSoYzavmylwuLWQOf3hl0jjMMIw==",
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/bindings": {
      "version": "1.5.0",
      "resolved": "https://registry.npmjs.org/bindings/-/bindings-1.5.0.tgz",
      "integrity": "sha512-p2q/t/mhvuOj/UeLlV6566GD/guowlr0hHxClI0W9m7MWYkL1F0hLo+0Aexs9HSPCtR1SXQ0TD3MMKrXZajbiQ==",
      "dependencies": {
        "file-uri-to-path": "1.0.0"
      }
    },
    "node_modules/bluebird": {
      "version": "3.7.2",
      "resolved": "https://registry.npmjs.org/bluebird/-/bluebird-3.7.2.tgz",
      "integrity": "sha512-XpNj6GDQzdfW+r2Wnn7xiSAd7TM3jzkxGXBGTtWKuSXv1xUV+azxAm8jdWZN06QTQk+2N2XB9jRDkvbmQmcRtg=="
    },
    "node_modules/bn.js": {
      "version": "5.2.1",
      "resolved": "https://registry.npmjs.org/bn.js/-/bn.js-5.2.1.tgz",
      "integrity": "sha512-eXRvHzWyYPBuB4NBy0cmYQjGitUrtqwbvlzP3G6VFnNRbsZQIxQ10PbKKHt8gZ/HW/D/747aDl+QkDqg3KQLMQ=="
    },
    "node_modules/borsh": {
      "version": "0.7.0",
      "resolved": "https://registry.npmjs.org/borsh/-/borsh-0.7.0.tgz",
      "integrity": "sha512-CLCsZGIBCFnPtkNnieW/a8wmreDmfUtjU2m9yHrzPXIlNbqVs0AQrSatSG6vdNYUqdc83tkQi2eHfF98ubzQLA==",
      "dependencies": {
        "bn.js": "^5.2.0",
        "bs58": "^4.0.0",
        "text-encoding-utf-8": "^1.0.2"
      }
    },
    "node_modules/bowser": {
      "version": "2.11.0",
      "resolved": "https://registry.npmjs.org/bowser/-/bowser-2.11.0.tgz",
      "integrity": "sha512-AlcaJBi/pqqJBIQ8U9Mcpc9i8Aqxn88Skv5d+xBX006BY5u8N3mGLHa5Lgppa7L/HfwgwLgZ6NYs+Ag6uUmJRA=="
    },
    "node_modules/brace-expansion": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/brace-expansion/-/brace-expansion-2.0.1.tgz",
      "integrity": "sha512-XnAIvQ8eM+kC6aULx6wuQiwVsnzsi9d3WxzV3FpWTGA19F621kwdbsAcFKXgKUHZWsy+mY6iL1sHTxWEFCytDA==",
      "dev": true,
      "dependencies": {
        "balanced-match": "^1.0.0"
      }
    },
    "node_modules/braces": {
      "version": "3.0.3",
      "resolved": "https://registry.npmjs.org/braces/-/braces-3.0.3.tgz",
      "integrity": "sha512-yQbXgO/OSZVD2IsiLlro+7Hf6Q18EJrKSEsdoMzKePKXct3gvD8oLcOQdIzGupr5Fj+EDe8gO/lxc1BzfMpxvA==",
      "dependencies": {
        "fill-range": "^7.1.1"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/brorand": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/brorand/-/brorand-1.1.0.tgz",
      "integrity": "sha512-cKV8tMCEpQs4hK/ik71d6LrPOnpkpGBR0wzxqr68g2m/LB2GxVYQroAjMJZRVM1Y4BCjCKc3vAamxSzOY2RP+w=="
    },
    "node_modules/browserslist": {
      "version": "4.24.2",
      "resolved": "https://registry.npmjs.org/browserslist/-/browserslist-4.24.2.tgz",
      "integrity": "sha512-ZIc+Q62revdMcqC6aChtW4jz3My3klmCO1fEmINZY/8J3EpBg5/A/D0AKmBveUh6pgoeycoMkVMko84tuYS+Gg==",
      "dev": true,
      "funding": [
        {
          "type": "opencollective",
          "url": "https://opencollective.com/browserslist"
        },
        {
          "type": "tidelift",
          "url": "https://tidelift.com/funding/github/npm/browserslist"
        },
        {
          "type": "github",
          "url": "https://github.com/sponsors/ai"
        }
      ],
      "dependencies": {
        "caniuse-lite": "^1.0.30001669",
        "electron-to-chromium": "^1.5.41",
        "node-releases": "^2.0.18",
        "update-browserslist-db": "^1.1.1"
      },
      "bin": {
        "browserslist": "cli.js"
      },
      "engines": {
        "node": "^6 || ^7 || ^8 || ^9 || ^10 || ^11 || ^12 || >=13.7"
      }
    },
    "node_modules/bs58": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/bs58/-/bs58-4.0.1.tgz",
      "integrity": "sha512-Ok3Wdf5vOIlBrgCvTq96gBkJw+JUEzdBgyaza5HLtPm7yTHkjRy8+JzNyHF7BHa0bNWOQIp3m5YF0nnFcOIKLw==",
      "dependencies": {
        "base-x": "^3.0.2"
      }
    },
    "node_modules/buffer": {
      "version": "6.0.3",
      "resolved": "https://registry.npmjs.org/buffer/-/buffer-6.0.3.tgz",
      "integrity": "sha512-FTiCpNxtwiZZHEZbcbTIcZjERVICn9yq/pDFkTl95/AxzD1naBctN7YO68riM/gLSDY7sdrMby8hofADYuuqOA==",
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/feross"
        },
        {
          "type": "patreon",
          "url": "https://www.patreon.com/feross"
        },
        {
          "type": "consulting",
          "url": "https://feross.org/support"
        }
      ],
      "dependencies": {
        "base64-js": "^1.3.1",
        "ieee754": "^1.2.1"
      }
    },
    "node_modules/bufferutil": {
      "version": "4.0.8",
      "resolved": "https://registry.npmjs.org/bufferutil/-/bufferutil-4.0.8.tgz",
      "integrity": "sha512-4T53u4PdgsXqKaIctwF8ifXlRTTmEPJ8iEPWFdGZvcf7sbwYo6FKFEX9eNNAnzFZ7EzJAQ3CJeOtCRA4rDp7Pw==",
      "hasInstallScript": true,
      "optional": true,
      "dependencies": {
        "node-gyp-build": "^4.3.0"
      },
      "engines": {
        "node": ">=6.14.2"
      }
    },
    "node_modules/call-bind": {
      "version": "1.0.7",
      "resolved": "https://registry.npmjs.org/call-bind/-/call-bind-1.0.7.tgz",
      "integrity": "sha512-GHTSNSYICQ7scH7sZ+M2rFopRoLh8t2bLSW6BbgrtLsahOIB5iyAVJf9GjWK3cYTDaMj4XdBpM1cA6pIS0Kv2w==",
      "dependencies": {
        "es-define-property": "^1.0.0",
        "es-errors": "^1.3.0",
        "function-bind": "^1.1.2",
        "get-intrinsic": "^1.2.4",
        "set-function-length": "^1.2.1"
      },
      "engines": {
        "node": ">= 0.4"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/callsites": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/callsites/-/callsites-3.1.0.tgz",
      "integrity": "sha512-P8BjAsXvZS+VIDUI11hHCQEv74YT67YUi5JJFNWIqL235sBmjX4+qx9Muvls5ivyNENctx46xQLQ3aTuE7ssaQ==",
      "dev": true,
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/camelcase": {
      "version": "5.3.1",
      "resolved": "https://registry.npmjs.org/camelcase/-/camelcase-5.3.1.tgz",
      "integrity": "sha512-L28STB170nwWS63UjtlEOE3dldQApaJXZkOI1uMFfzf3rRuPegHaHesyee+YxQ+W6SvRDQV6UrdOdRiR153wJg==",
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/camelcase-css": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/camelcase-css/-/camelcase-css-2.0.1.tgz",
      "integrity": "sha512-QOSvevhslijgYwRx6Rv7zKdMF8lbRmx+uQGx2+vDc+KI/eBnsy9kit5aj23AgGu3pa4t9AgwbnXWqS+iOY+2aA==",
      "dev": true,
      "engines": {
        "node": ">= 6"
      }
    },
    "node_modules/caniuse-lite": {
      "version": "1.0.30001676",
      "resolved": "https://registry.npmjs.org/caniuse-lite/-/caniuse-lite-1.0.30001676.tgz",
      "integrity": "sha512-Qz6zwGCiPghQXGJvgQAem79esjitvJ+CxSbSQkW9H/UX5hg8XM88d4lp2W+MEQ81j+Hip58Il+jGVdazk1z9cw==",
      "dev": true,
      "funding": [
        {
          "type": "opencollective",
          "url": "https://opencollective.com/browserslist"
        },
        {
          "type": "tidelift",
          "url": "https://tidelift.com/funding/github/npm/caniuse-lite"
        },
        {
          "type": "github",
          "url": "https://github.com/sponsors/ai"
        }
      ]
    },
    "node_modules/chalk": {
      "version": "4.1.2",
      "resolved": "https://registry.npmjs.org/chalk/-/chalk-4.1.2.tgz",
      "integrity": "sha512-oKnbhFyRIXpUuez8iBMmyEa4nbj4IOQyuhc/wy9kY7/WVPcwIO9VA668Pu8RkO7+0G76SLROeyw9CpQ061i4mA==",
      "dev": true,
      "dependencies": {
        "ansi-styles": "^4.1.0",
        "supports-color": "^7.1.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/chalk/chalk?sponsor=1"
      }
    },
    "node_modules/check-more-types": {
      "version": "2.24.0",
      "resolved": "https://registry.npmjs.org/check-more-types/-/check-more-types-2.24.0.tgz",
      "integrity": "sha512-Pj779qHxV2tuapviy1bSZNEL1maXr13bPYpsvSDB68HlYcYuhlDrmGd63i0JHMCLKzc7rUSNIrpdJlhVlNwrxA==",
      "engines": {
        "node": ">= 0.8.0"
      }
    },
    "node_modules/chokidar": {
      "version": "3.6.0",
      "resolved": "https://registry.npmjs.org/chokidar/-/chokidar-3.6.0.tgz",
      "integrity": "sha512-7VT13fmjotKpGipCW9JEQAusEPE+Ei8nl6/g4FBAmIm0GOOLMua9NDDo/DWp0ZAxCr3cPq5ZpBqmPAQgDda2Pw==",
      "dependencies": {
        "anymatch": "~3.1.2",
        "braces": "~3.0.2",
        "glob-parent": "~5.1.2",
        "is-binary-path": "~2.1.0",
        "is-glob": "~4.0.1",
        "normalize-path": "~3.0.0",
        "readdirp": "~3.6.0"
      },
      "engines": {
        "node": ">= 8.10.0"
      },
      "funding": {
        "url": "https://paulmillr.com/funding/"
      },
      "optionalDependencies": {
        "fsevents": "~2.3.2"
      }
    },
    "node_modules/chokidar/node_modules/glob-parent": {
      "version": "5.1.2",
      "resolved": "https://registry.npmjs.org/glob-parent/-/glob-parent-5.1.2.tgz",
      "integrity": "sha512-AOIgSQCepiJYwP3ARnGx+5VnTu2HBYdzbGP45eLw1vr3zB3vZLeyed1sC9hnbcOc9/SrMyM5RPQrkGz4aS9Zow==",
      "dependencies": {
        "is-glob": "^4.0.1"
      },
      "engines": {
        "node": ">= 6"
      }
    },
    "node_modules/citty": {
      "version": "0.1.6",
      "resolved": "https://registry.npmjs.org/citty/-/citty-0.1.6.tgz",
      "integrity": "sha512-tskPPKEs8D2KPafUypv2gxwJP8h/OaJmC82QQGGDQcHvXX43xF2VDACcJVmZ0EuSxkpO9Kc4MlrA3q0+FG58AQ==",
      "dependencies": {
        "consola": "^3.2.3"
      }
    },
    "node_modules/classnames": {
      "version": "2.5.1",
      "resolved": "https://registry.npmjs.org/classnames/-/classnames-2.5.1.tgz",
      "integrity": "sha512-saHYOzhIQs6wy2sVxTM6bUDsQO4F50V9RQ22qBpEdCW+I+/Wmke2HOl6lS6dTpdxVhb88/I6+Hs+438c3lfUow=="
    },
    "node_modules/clipboardy": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/clipboardy/-/clipboardy-4.0.0.tgz",
      "integrity": "sha512-5mOlNS0mhX0707P2I0aZ2V/cmHUEO/fL7VFLqszkhUsxt7RwnmrInf/eEQKlf5GzvYeHIjT+Ov1HRfNmymlG0w==",
      "dependencies": {
        "execa": "^8.0.1",
        "is-wsl": "^3.1.0",
        "is64bit": "^2.0.0"
      },
      "engines": {
        "node": ">=18"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/cliui": {
      "version": "6.0.0",
      "resolved": "https://registry.npmjs.org/cliui/-/cliui-6.0.0.tgz",
      "integrity": "sha512-t6wbgtoCXvAzst7QgXxJYqPt0usEfbgQdftEPbLL/cvv6HPE5VgvqCuAIDR0NgU52ds6rFwqrgakNLrHEjCbrQ==",
      "dependencies": {
        "string-width": "^4.2.0",
        "strip-ansi": "^6.0.0",
        "wrap-ansi": "^6.2.0"
      }
    },
    "node_modules/clsx": {
      "version": "1.2.1",
      "resolved": "https://registry.npmjs.org/clsx/-/clsx-1.2.1.tgz",
      "integrity": "sha512-EcR6r5a8bj6pu3ycsa/E/cKVGuTgZJZdsyUYHOksG/UHIiKfjxzRxYJpyVBwYaQeOvghal9fcc4PidlgzugAQg==",
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/code-point-at": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/code-point-at/-/code-point-at-1.1.0.tgz",
      "integrity": "sha512-RpAVKQA5T63xEj6/giIbUEtZwJ4UFIc3ZtvEkiaUERylqe8xb5IvqcgOurZLahv93CLKfxcw5YI+DZcUBRyLXA==",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/color-convert": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/color-convert/-/color-convert-2.0.1.tgz",
      "integrity": "sha512-RRECPsj7iu/xb5oKYcsFHSppFNnsj/52OVTRKb4zP5onXwVF3zVmmToNcOfGC+CRDpfK/U584fMg38ZHCaElKQ==",
      "dependencies": {
        "color-name": "~1.1.4"
      },
      "engines": {
        "node": ">=7.0.0"
      }
    },
    "node_modules/color-name": {
      "version": "1.1.4",
      "resolved": "https://registry.npmjs.org/color-name/-/color-name-1.1.4.tgz",
      "integrity": "sha512-dOy+3AuW3a2wNbZHIuMZpTcgjGuLU/uBL/ubcZF9OXbDo8ff4O8yVp5Bf0efS8uEoYo5q4Fx7dY9OgQGXgAsQA=="
    },
    "node_modules/combined-stream": {
      "version": "1.0.8",
      "resolved": "https://registry.npmjs.org/combined-stream/-/combined-stream-1.0.8.tgz",
      "integrity": "sha512-FQN4MRfuJeHf7cBbBMJFXhKSDq+2kAArBlmRBvcvFE5BB1HZKXtSFASDhdlz9zOYwxh8lDdnvmMOe/+5cdoEdg==",
      "dependencies": {
        "delayed-stream": "~1.0.0"
      },
      "engines": {
        "node": ">= 0.8"
      }
    },
    "node_modules/commander": {
      "version": "2.20.3",
      "resolved": "https://registry.npmjs.org/commander/-/commander-2.20.3.tgz",
      "integrity": "sha512-GpVkmM8vF2vQUkj2LvZmD35JxeJOLCwJ9cUkugyk2nuhbv3+mJvpLYYt+0+USMxE+oj+ey/lJEnhZw75x/OMcQ=="
    },
    "node_modules/compute-scroll-into-view": {
      "version": "1.0.20",
      "resolved": "https://registry.npmjs.org/compute-scroll-into-view/-/compute-scroll-into-view-1.0.20.tgz",
      "integrity": "sha512-UCB0ioiyj8CRjtrvaceBLqqhZCVP+1B8+NWQhmdsm0VXOJtobBCf1dBQmebCCo34qZmUwZfIH2MZLqNHazrfjg=="
    },
    "node_modules/concat-map": {
      "version": "0.0.1",
      "resolved": "https://registry.npmjs.org/concat-map/-/concat-map-0.0.1.tgz",
      "integrity": "sha512-/Srv4dswyQNBfohGpz9o6Yb3Gz3SrUDqBH5rTuhGR7ahtlbYKnVxw2bCFMRljaA7EXHaXZ8wsHdodFvbkhKmqg==",
      "dev": true
    },
    "node_modules/confbox": {
      "version": "0.1.8",
      "resolved": "https://registry.npmjs.org/confbox/-/confbox-0.1.8.tgz",
      "integrity": "sha512-RMtmw0iFkeR4YV+fUOSucriAQNb9g8zFR52MWCtl+cCZOFRNL6zeB395vPzFhEjjn4fMxXudmELnl/KF/WrK6w=="
    },
    "node_modules/consola": {
      "version": "3.2.3",
      "resolved": "https://registry.npmjs.org/consola/-/consola-3.2.3.tgz",
      "integrity": "sha512-I5qxpzLv+sJhTVEoLYNcTW+bThDCPsit0vLNKShZx6rLtpilNpmmeTPaeqJb9ZE9dV3DGaeby6Vuhrw38WjeyQ==",
      "engines": {
        "node": "^14.18.0 || >=16.10.0"
      }
    },
    "node_modules/content-type": {
      "version": "1.0.5",
      "resolved": "https://registry.npmjs.org/content-type/-/content-type-1.0.5.tgz",
      "integrity": "sha512-nTjqfcBFEipKdXCv4YDQWCfmcLZKm81ldF0pAopTvyrFGVbcR6P/VAAd5G7N+0tTr8QqiU0tFadD6FK4NtJwOA==",
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/convert-source-map": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/convert-source-map/-/convert-source-map-2.0.0.tgz",
      "integrity": "sha512-Kvp459HrV2FEJ1CAsi1Ku+MY3kasH19TFykTz2xWmMeq6bk2NU3XXvfJ+Q61m0xktWwt+1HSYf3JZsTms3aRJg==",
      "dev": true
    },
    "node_modules/cookie-es": {
      "version": "1.2.2",
      "resolved": "https://registry.npmjs.org/cookie-es/-/cookie-es-1.2.2.tgz",
      "integrity": "sha512-+W7VmiVINB+ywl1HGXJXmrqkOhpKrIiVZV6tQuV54ZyQC7MMuBt81Vc336GMLoHBq5hV/F9eXgt5Mnx0Rha5Fg=="
    },
    "node_modules/copy-to-clipboard": {
      "version": "3.3.3",
      "resolved": "https://registry.npmjs.org/copy-to-clipboard/-/copy-to-clipboard-3.3.3.tgz",
      "integrity": "sha512-2KV8NhB5JqC3ky0r9PMCAZKbUHSwtEo4CwCs0KXgruG43gX5PMqDEBbVU4OUzw2MuAWUfsuFmWvEKG5QRfSnJA==",
      "dependencies": {
        "toggle-selection": "^1.0.6"
      }
    },
    "node_modules/country-flag-icons": {
      "version": "1.5.13",
      "resolved": "https://registry.npmjs.org/country-flag-icons/-/country-flag-icons-1.5.13.tgz",
      "integrity": "sha512-4JwHNqaKZ19doQoNcBjsoYA+I7NqCH/mC/6f5cBWvdKzcK5TMmzLpq3Z/syVHMHJuDGFwJ+rPpGizvrqJybJow=="
    },
    "node_modules/crc-32": {
      "version": "1.2.2",
      "resolved": "https://registry.npmjs.org/crc-32/-/crc-32-1.2.2.tgz",
      "integrity": "sha512-ROmzCKrTnOwybPcJApAA6WBWij23HVfGVNKqqrZpuyZOHqK2CwHSvpGuyt/UNNvaIjEd8X5IFGp4Mh+Ie1IHJQ==",
      "bin": {
        "crc32": "bin/crc32.njs"
      },
      "engines": {
        "node": ">=0.8"
      }
    },
    "node_modules/cross-fetch": {
      "version": "3.1.8",
      "resolved": "https://registry.npmjs.org/cross-fetch/-/cross-fetch-3.1.8.tgz",
      "integrity": "sha512-cvA+JwZoU0Xq+h6WkMvAUqPEYy92Obet6UdKLfW60qn99ftItKjB5T+BkyWOFWe2pUyfQ+IJHmpOTznqk1M6Kg==",
      "dependencies": {
        "node-fetch": "^2.6.12"
      }
    },
    "node_modules/cross-spawn": {
      "version": "7.0.3",
      "resolved": "https://registry.npmjs.org/cross-spawn/-/cross-spawn-7.0.3.tgz",
      "integrity": "sha512-iRDPJKUPVEND7dHPO8rkbOnPpyDygcDFtWjpeWNCgy8WP2rXcxXL8TskReQl6OrB2G7+UJrags1q15Fudc7G6w==",
      "dependencies": {
        "path-key": "^3.1.0",
        "shebang-command": "^2.0.0",
        "which": "^2.0.1"
      },
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/crossws": {
      "version": "0.3.1",
      "resolved": "https://registry.npmjs.org/crossws/-/crossws-0.3.1.tgz",
      "integrity": "sha512-HsZgeVYaG+b5zA+9PbIPGq4+J/CJynJuearykPsXx4V/eMhyQ5EDVg3Ak2FBZtVXCiOLu/U7IiwDHTr9MA+IKw==",
      "dependencies": {
        "uncrypto": "^0.1.3"
      }
    },
    "node_modules/crypto-js": {
      "version": "4.2.0",
      "resolved": "https://registry.npmjs.org/crypto-js/-/crypto-js-4.2.0.tgz",
      "integrity": "sha512-KALDyEYgpY+Rlob/iriUtjV6d5Eq+Y191A5g4UqLAi8CyGP9N1+FdVbkc1SxKc2r4YAYqG8JzO2KGL+AizD70Q=="
    },
    "node_modules/css-selector-tokenizer": {
      "version": "0.8.0",
      "resolved": "https://registry.npmjs.org/css-selector-tokenizer/-/css-selector-tokenizer-0.8.0.tgz",
      "integrity": "sha512-Jd6Ig3/pe62/qe5SBPTN8h8LeUg/pT4lLgtavPf7updwwHpvFzxvOQBHYj2LZDMjUnBzgvIUSjRcf6oT5HzHFg==",
      "dev": true,
      "dependencies": {
        "cssesc": "^3.0.0",
        "fastparse": "^1.1.2"
      }
    },
    "node_modules/cssesc": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/cssesc/-/cssesc-3.0.0.tgz",
      "integrity": "sha512-/Tb/JcjK111nNScGob5MNtsntNM1aCNUDipB/TkwZFhyDrrE47SOx/18wF2bbjgc3ZzCSKW1T5nt5EbFoAz/Vg==",
      "dev": true,
      "bin": {
        "cssesc": "bin/cssesc"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/csstype": {
      "version": "3.1.3",
      "resolved": "https://registry.npmjs.org/csstype/-/csstype-3.1.3.tgz",
      "integrity": "sha512-M1uQkMl8rQK/szD0LNhtqxIPLpimGm8sOBwU7lLnCpSbTyY3yeU1Vc7l4KT5zT4s/yOxHH5O7tIuuLOCnLADRw==",
      "devOptional": true
    },
    "node_modules/culori": {
      "version": "3.3.0",
      "resolved": "https://registry.npmjs.org/culori/-/culori-3.3.0.tgz",
      "integrity": "sha512-pHJg+jbuFsCjz9iclQBqyL3B2HLCBF71BwVNujUYEvCeQMvV97R59MNK3R2+jgJ3a1fcZgI9B3vYgz8lzr/BFQ==",
      "dev": true,
      "engines": {
        "node": "^12.20.0 || ^14.13.1 || >=16.0.0"
      }
    },
    "node_modules/daisyui": {
      "version": "4.12.14",
      "resolved": "https://registry.npmjs.org/daisyui/-/daisyui-4.12.14.tgz",
      "integrity": "sha512-hA27cdBasdwd4/iEjn+aidoCrRroDuo3G5W9NDKaVCJI437Mm/3eSL/2u7MkZ0pt8a+TrYF3aT2pFVemTS3how==",
      "dev": true,
      "dependencies": {
        "css-selector-tokenizer": "^0.8",
        "culori": "^3",
        "picocolors": "^1",
        "postcss-js": "^4"
      },
      "engines": {
        "node": ">=16.9.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/daisyui"
      }
    },
    "node_modules/date-fns": {
      "version": "2.30.0",
      "resolved": "https://registry.npmjs.org/date-fns/-/date-fns-2.30.0.tgz",
      "integrity": "sha512-fnULvOpxnC5/Vg3NCiWelDsLiUc9bRwAPs/+LfTLNvetFCtCTN+yQz15C/fs4AwX1R9K5GLtLfn8QW+dWisaAw==",
      "dependencies": {
        "@babel/runtime": "^7.21.0"
      },
      "engines": {
        "node": ">=0.11"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/date-fns"
      }
    },
    "node_modules/dayjs": {
      "version": "1.11.13",
      "resolved": "https://registry.npmjs.org/dayjs/-/dayjs-1.11.13.tgz",
      "integrity": "sha512-oaMBel6gjolK862uaPQOVTA7q3TZhuSvuMQAAglQDOWYO9A91IrAOUJEyKVlqJlHE0vq5p5UXxzdPfMH/x6xNg=="
    },
    "node_modules/debug": {
      "version": "4.3.7",
      "resolved": "https://registry.npmjs.org/debug/-/debug-4.3.7.tgz",
      "integrity": "sha512-Er2nc/H7RrMXZBFCEim6TCmMk02Z8vLC2Rbi1KEBggpo0fS6l0S1nnapwmIi3yW/+GOJap1Krg4w0Hg80oCqgQ==",
      "dependencies": {
        "ms": "^2.1.3"
      },
      "engines": {
        "node": ">=6.0"
      },
      "peerDependenciesMeta": {
        "supports-color": {
          "optional": true
        }
      }
    },
    "node_modules/decamelize": {
      "version": "1.2.0",
      "resolved": "https://registry.npmjs.org/decamelize/-/decamelize-1.2.0.tgz",
      "integrity": "sha512-z2S+W9X73hAUUki+N+9Za2lBlun89zigOyGrsax+KUQ6wKW4ZoWpEYBkGhQjwAjjDCkWxhY0VKEhk8wzY7F5cA==",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/decode-uri-component": {
      "version": "0.2.2",
      "resolved": "https://registry.npmjs.org/decode-uri-component/-/decode-uri-component-0.2.2.tgz",
      "integrity": "sha512-FqUYQ+8o158GyGTrMFJms9qh3CqTKvAqgqsTnkLI8sKu0028orqBhxNMFkFen0zGyg6epACD32pjVk58ngIErQ==",
      "engines": {
        "node": ">=0.10"
      }
    },
    "node_modules/deep-is": {
      "version": "0.1.4",
      "resolved": "https://registry.npmjs.org/deep-is/-/deep-is-0.1.4.tgz",
      "integrity": "sha512-oIPzksmTg4/MriiaYGO+okXDT7ztn/w3Eptv/+gSIdMdKsJo0u4CfYNFJPy+4SKMuCqGw2wxnA+URMg3t8a/bQ==",
      "dev": true
    },
    "node_modules/define-data-property": {
      "version": "1.1.4",
      "resolved": "https://registry.npmjs.org/define-data-property/-/define-data-property-1.1.4.tgz",
      "integrity": "sha512-rBMvIzlpA8v6E+SJZoo++HAYqsLrkg7MSfIinMPFhmkorw7X+dOXVJQs+QT69zGkzMyfDnIMN2Wid1+NbL3T+A==",
      "dependencies": {
        "es-define-property": "^1.0.0",
        "es-errors": "^1.3.0",
        "gopd": "^1.0.1"
      },
      "engines": {
        "node": ">= 0.4"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/defu": {
      "version": "6.1.4",
      "resolved": "https://registry.npmjs.org/defu/-/defu-6.1.4.tgz",
      "integrity": "sha512-mEQCMmwJu317oSz8CwdIOdwf3xMif1ttiM8LTufzc3g6kR+9Pe236twL8j3IYT1F7GfRgGcW6MWxzZjLIkuHIg=="
    },
    "node_modules/delay": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/delay/-/delay-5.0.0.tgz",
      "integrity": "sha512-ReEBKkIfe4ya47wlPYf/gu5ib6yUG0/Aez0JQZQz94kiWtRQvZIQbTiehsnwHvLSWJnQdhVeqYue7Id1dKr0qw==",
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/delayed-stream": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/delayed-stream/-/delayed-stream-1.0.0.tgz",
      "integrity": "sha512-ZySD7Nf91aLB0RxL4KGrKHBXl7Eds1DAmEdcoVawXnLD7SDhpNgtuII2aAkg7a7QS41jxPSZ17p4VdGnMHk3MQ==",
      "engines": {
        "node": ">=0.4.0"
      }
    },
    "node_modules/destr": {
      "version": "2.0.3",
      "resolved": "https://registry.npmjs.org/destr/-/destr-2.0.3.tgz",
      "integrity": "sha512-2N3BOUU4gYMpTP24s5rF5iP7BDr7uNTCs4ozw3kf/eKfvWSIu93GEBi5m427YoyJoeOzQ5smuu4nNAPGb8idSQ=="
    },
    "node_modules/detect-browser": {
      "version": "5.3.0",
      "resolved": "https://registry.npmjs.org/detect-browser/-/detect-browser-5.3.0.tgz",
      "integrity": "sha512-53rsFbGdwMwlF7qvCt0ypLM5V5/Mbl0szB7GPN8y9NCcbknYOeVVXdrXEq+90IwAfrrzt6Hd+u2E2ntakICU8w=="
    },
    "node_modules/detect-libc": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/detect-libc/-/detect-libc-1.0.3.tgz",
      "integrity": "sha512-pGjwhsmsp4kL2RTz08wcOlGN83otlqHeD/Z5T8GXZB+/YcpQ/dgo+lbU8ZsGxV0HIvqqxo9l7mqYwyYMD9bKDg==",
      "bin": {
        "detect-libc": "bin/detect-libc.js"
      },
      "engines": {
        "node": ">=0.10"
      }
    },
    "node_modules/didyoumean": {
      "version": "1.2.2",
      "resolved": "https://registry.npmjs.org/didyoumean/-/didyoumean-1.2.2.tgz",
      "integrity": "sha512-gxtyfqMg7GKyhQmb056K7M3xszy/myH8w+B4RT+QXBQsvAOdc3XymqDDPHx1BgPgsdAA5SIifona89YtRATDzw==",
      "dev": true
    },
    "node_modules/dijkstrajs": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/dijkstrajs/-/dijkstrajs-1.0.3.tgz",
      "integrity": "sha512-qiSlmBq9+BCdCA/L46dw8Uy93mloxsPSbwnm5yrKn2vMPiy8KyAskTF6zuV/j5BMsmOGZDPs7KjU+mjb670kfA=="
    },
    "node_modules/dir-glob": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/dir-glob/-/dir-glob-3.0.1.tgz",
      "integrity": "sha512-WkrWp9GR4KXfKGYzOLmTuGVi1UWFfws377n9cc55/tb6DuqyF6pcQ5AbiHEshaDpY9v6oaSr2XCDidGmMwdzIA==",
      "dev": true,
      "dependencies": {
        "path-type": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/dlv": {
      "version": "1.1.3",
      "resolved": "https://registry.npmjs.org/dlv/-/dlv-1.1.3.tgz",
      "integrity": "sha512-+HlytyjlPKnIG8XuRG8WvmBP8xs8P71y+SKKS6ZXWoEgLuePxtDoUEiH7WkdePWrQ5JBpE6aoVqfZfJUQkjXwA==",
      "dev": true
    },
    "node_modules/doctrine": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/doctrine/-/doctrine-3.0.0.tgz",
      "integrity": "sha512-yS+Q5i3hBf7GBkd4KG8a7eBNNWNGLTaEwwYWUijIYM7zrlYDM0BFXHjjPWlWZ1Rg7UaddZeIDmi9jF3HmqiQ2w==",
      "dev": true,
      "dependencies": {
        "esutils": "^2.0.2"
      },
      "engines": {
        "node": ">=6.0.0"
      }
    },
    "node_modules/dom-align": {
      "version": "1.12.4",
      "resolved": "https://registry.npmjs.org/dom-align/-/dom-align-1.12.4.tgz",
      "integrity": "sha512-R8LUSEay/68zE5c8/3BDxiTEvgb4xZTF0RKmAHfiEVN3klfIpXfi2/QCoiWPccVQ0J/ZGdz9OjzL4uJEP/MRAw=="
    },
    "node_modules/draggabilly": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/draggabilly/-/draggabilly-3.0.0.tgz",
      "integrity": "sha512-aEs+B6prbMZQMxc9lgTpCBfyCUhRur/VFucHhIOvlvvdARTj7TcDmX/cdOUtqbjJJUh7+agyJXR5Z6IFe1MxwQ==",
      "dependencies": {
        "get-size": "^3.0.0",
        "unidragger": "^3.0.0"
      }
    },
    "node_modules/duplexer": {
      "version": "0.1.2",
      "resolved": "https://registry.npmjs.org/duplexer/-/duplexer-0.1.2.tgz",
      "integrity": "sha512-jtD6YG370ZCIi/9GTaJKQxWTZD045+4R4hTk/x1UyoqadyJ9x9CgSi1RlVDQF8U2sxLLSnFkCaMihqljHIWgMg=="
    },
    "node_modules/duplexify": {
      "version": "4.1.3",
      "resolved": "https://registry.npmjs.org/duplexify/-/duplexify-4.1.3.tgz",
      "integrity": "sha512-M3BmBhwJRZsSx38lZyhE53Csddgzl5R7xGJNk7CVddZD6CcmwMCH8J+7AprIrQKH7TonKxaCjcv27Qmf+sQ+oA==",
      "dependencies": {
        "end-of-stream": "^1.4.1",
        "inherits": "^2.0.3",
        "readable-stream": "^3.1.1",
        "stream-shift": "^1.0.2"
      }
    },
    "node_modules/eastasianwidth": {
      "version": "0.2.0",
      "resolved": "https://registry.npmjs.org/eastasianwidth/-/eastasianwidth-0.2.0.tgz",
      "integrity": "sha512-I88TYZWc9XiYHRQ4/3c5rjjfgkjhLyW2luGIheGERbNQ6OY7yTybanSpDXZa8y7VUP9YmDcYa+eyq4ca7iLqWA==",
      "dev": true
    },
    "node_modules/electron-to-chromium": {
      "version": "1.5.50",
      "resolved": "https://registry.npmjs.org/electron-to-chromium/-/electron-to-chromium-1.5.50.tgz",
      "integrity": "sha512-eMVObiUQ2LdgeO1F/ySTXsvqvxb6ZH2zPGaMYsWzRDdOddUa77tdmI0ltg+L16UpbWdhPmuF3wIQYyQq65WfZw==",
      "dev": true
    },
    "node_modules/elliptic": {
      "version": "6.6.0",
      "resolved": "https://registry.npmjs.org/elliptic/-/elliptic-6.6.0.tgz",
      "integrity": "sha512-dpwoQcLc/2WLQvJvLRHKZ+f9FgOdjnq11rurqwekGQygGPsYSK29OMMD2WalatiqQ+XGFDglTNixpPfI+lpaAA==",
      "dependencies": {
        "bn.js": "^4.11.9",
        "brorand": "^1.1.0",
        "hash.js": "^1.0.0",
        "hmac-drbg": "^1.0.1",
        "inherits": "^2.0.4",
        "minimalistic-assert": "^1.0.1",
        "minimalistic-crypto-utils": "^1.0.1"
      }
    },
    "node_modules/elliptic/node_modules/bn.js": {
      "version": "4.12.0",
      "resolved": "https://registry.npmjs.org/bn.js/-/bn.js-4.12.0.tgz",
      "integrity": "sha512-c98Bf3tPniI+scsdk237ku1Dc3ujXQTSgyiPUDEOe7tRkhrqridvh8klBv0HCEso1OLOYcHuCv/cS6DNxKH+ZA=="
    },
    "node_modules/emoji-regex": {
      "version": "8.0.0",
      "resolved": "https://registry.npmjs.org/emoji-regex/-/emoji-regex-8.0.0.tgz",
      "integrity": "sha512-MSjYzcWNOA0ewAHpz0MxpYFvwg6yjy1NG3xteoqz644VCo/RPgnr1/GGt+ic3iJTzQ8Eu3TdM14SawnVUmGE6A=="
    },
    "node_modules/encode-utf8": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/encode-utf8/-/encode-utf8-1.0.3.tgz",
      "integrity": "sha512-ucAnuBEhUK4boH2HjVYG5Q2mQyPorvv0u/ocS+zhdw0S8AlHYY+GOFhP1Gio5z4icpP2ivFSvhtFjQi8+T9ppw=="
    },
    "node_modules/end-of-stream": {
      "version": "1.4.4",
      "resolved": "https://registry.npmjs.org/end-of-stream/-/end-of-stream-1.4.4.tgz",
      "integrity": "sha512-+uw1inIHVPQoaVuHzRyXd21icM+cnt4CzD5rW+NC1wjOUSTOs+Te7FOv7AhN7vS9x/oIyhLP5PR1H+phQAHu5Q==",
      "dependencies": {
        "once": "^1.4.0"
      }
    },
    "node_modules/es-define-property": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/es-define-property/-/es-define-property-1.0.0.tgz",
      "integrity": "sha512-jxayLKShrEqqzJ0eumQbVhTYQM27CfT1T35+gCgDFoL82JLsXqTJ76zv6A0YLOgEnLUMvLzsDsGIrl8NFpT2gQ==",
      "dependencies": {
        "get-intrinsic": "^1.2.4"
      },
      "engines": {
        "node": ">= 0.4"
      }
    },
    "node_modules/es-errors": {
      "version": "1.3.0",
      "resolved": "https://registry.npmjs.org/es-errors/-/es-errors-1.3.0.tgz",
      "integrity": "sha512-Zf5H2Kxt2xjTvbJvP2ZWLEICxA6j+hAmMzIlypy4xcBg1vKVnx89Wy0GbS+kf5cwCVFFzdCFh2XSCFNULS6csw==",
      "engines": {
        "node": ">= 0.4"
      }
    },
    "node_modules/es6-promise": {
      "version": "4.2.8",
      "resolved": "https://registry.npmjs.org/es6-promise/-/es6-promise-4.2.8.tgz",
      "integrity": "sha512-HJDGx5daxeIvxdBxvG2cb9g4tEvwIk3i8+nhX0yGrYmZUzbkdg8QbDevheDB8gd0//uPj4c1EQua8Q+MViT0/w=="
    },
    "node_modules/es6-promisify": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/es6-promisify/-/es6-promisify-5.0.0.tgz",
      "integrity": "sha512-C+d6UdsYDk0lMebHNR4S2NybQMMngAOnOwYBQjTOiv0MkoJMP0Myw2mgpDLBcpfCmRLxyFqYhS/CfOENq4SJhQ==",
      "dependencies": {
        "es6-promise": "^4.0.3"
      }
    },
    "node_modules/esbuild": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/esbuild/-/esbuild-0.21.5.tgz",
      "integrity": "sha512-mg3OPMV4hXywwpoDxu3Qda5xCKQi+vCTZq8S9J/EpkhB2HzKXq4SNFZE3+NK93JYxc8VMSep+lOUSC/RVKaBqw==",
      "dev": true,
      "hasInstallScript": true,
      "bin": {
        "esbuild": "bin/esbuild"
      },
      "engines": {
        "node": ">=12"
      },
      "optionalDependencies": {
        "@esbuild/aix-ppc64": "0.21.5",
        "@esbuild/android-arm": "0.21.5",
        "@esbuild/android-arm64": "0.21.5",
        "@esbuild/android-x64": "0.21.5",
        "@esbuild/darwin-arm64": "0.21.5",
        "@esbuild/darwin-x64": "0.21.5",
        "@esbuild/freebsd-arm64": "0.21.5",
        "@esbuild/freebsd-x64": "0.21.5",
        "@esbuild/linux-arm": "0.21.5",
        "@esbuild/linux-arm64": "0.21.5",
        "@esbuild/linux-ia32": "0.21.5",
        "@esbuild/linux-loong64": "0.21.5",
        "@esbuild/linux-mips64el": "0.21.5",
        "@esbuild/linux-ppc64": "0.21.5",
        "@esbuild/linux-riscv64": "0.21.5",
        "@esbuild/linux-s390x": "0.21.5",
        "@esbuild/linux-x64": "0.21.5",
        "@esbuild/netbsd-x64": "0.21.5",
        "@esbuild/openbsd-x64": "0.21.5",
        "@esbuild/sunos-x64": "0.21.5",
        "@esbuild/win32-arm64": "0.21.5",
        "@esbuild/win32-ia32": "0.21.5",
        "@esbuild/win32-x64": "0.21.5"
      }
    },
    "node_modules/escalade": {
      "version": "3.2.0",
      "resolved": "https://registry.npmjs.org/escalade/-/escalade-3.2.0.tgz",
      "integrity": "sha512-WUj2qlxaQtO4g6Pq5c29GTcWGDyd8itL8zTlipgECz3JesAiiOKotd8JU6otB3PACgG6xkJUyVhboMS+bje/jA==",
      "dev": true,
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/escape-string-regexp": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/escape-string-regexp/-/escape-string-regexp-4.0.0.tgz",
      "integrity": "sha512-TtpcNJ3XAzx3Gq8sWRzJaVajRs0uVxA2YAkdb1jm2YkPz4G6egUFAyA3n5vtEIZefPk5Wa4UXbKuS5fKkJWdgA==",
      "dev": true,
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/eslint": {
      "version": "8.57.1",
      "resolved": "https://registry.npmjs.org/eslint/-/eslint-8.57.1.tgz",
      "integrity": "sha512-ypowyDxpVSYpkXr9WPv2PAZCtNip1Mv5KTW0SCurXv/9iOpcrH9PaqUElksqEB6pChqHGDRCFTyrZlGhnLNGiA==",
      "deprecated": "This version is no longer supported. Please see https://eslint.org/version-support for other options.",
      "dev": true,
      "dependencies": {
        "@eslint-community/eslint-utils": "^4.2.0",
        "@eslint-community/regexpp": "^4.6.1",
        "@eslint/eslintrc": "^2.1.4",
        "@eslint/js": "8.57.1",
        "@humanwhocodes/config-array": "^0.13.0",
        "@humanwhocodes/module-importer": "^1.0.1",
        "@nodelib/fs.walk": "^1.2.8",
        "@ungap/structured-clone": "^1.2.0",
        "ajv": "^6.12.4",
        "chalk": "^4.0.0",
        "cross-spawn": "^7.0.2",
        "debug": "^4.3.2",
        "doctrine": "^3.0.0",
        "escape-string-regexp": "^4.0.0",
        "eslint-scope": "^7.2.2",
        "eslint-visitor-keys": "^3.4.3",
        "espree": "^9.6.1",
        "esquery": "^1.4.2",
        "esutils": "^2.0.2",
        "fast-deep-equal": "^3.1.3",
        "file-entry-cache": "^6.0.1",
        "find-up": "^5.0.0",
        "glob-parent": "^6.0.2",
        "globals": "^13.19.0",
        "graphemer": "^1.4.0",
        "ignore": "^5.2.0",
        "imurmurhash": "^0.1.4",
        "is-glob": "^4.0.0",
        "is-path-inside": "^3.0.3",
        "js-yaml": "^4.1.0",
        "json-stable-stringify-without-jsonify": "^1.0.1",
        "levn": "^0.4.1",
        "lodash.merge": "^4.6.2",
        "minimatch": "^3.1.2",
        "natural-compare": "^1.4.0",
        "optionator": "^0.9.3",
        "strip-ansi": "^6.0.1",
        "text-table": "^0.2.0"
      },
      "bin": {
        "eslint": "bin/eslint.js"
      },
      "engines": {
        "node": "^12.22.0 || ^14.17.0 || >=16.0.0"
      },
      "funding": {
        "url": "https://opencollective.com/eslint"
      }
    },
    "node_modules/eslint-plugin-react-hooks": {
      "version": "4.6.2",
      "resolved": "https://registry.npmjs.org/eslint-plugin-react-hooks/-/eslint-plugin-react-hooks-4.6.2.tgz",
      "integrity": "sha512-QzliNJq4GinDBcD8gPB5v0wh6g8q3SUi6EFF0x8N/BL9PoVs0atuGc47ozMRyOWAKdwaZ5OnbOEa3WR+dSGKuQ==",
      "dev": true,
      "engines": {
        "node": ">=10"
      },
      "peerDependencies": {
        "eslint": "^3.0.0 || ^4.0.0 || ^5.0.0 || ^6.0.0 || ^7.0.0 || ^8.0.0-0"
      }
    },
    "node_modules/eslint-plugin-react-refresh": {
      "version": "0.4.14",
      "resolved": "https://registry.npmjs.org/eslint-plugin-react-refresh/-/eslint-plugin-react-refresh-0.4.14.tgz",
      "integrity": "sha512-aXvzCTK7ZBv1e7fahFuR3Z/fyQQSIQ711yPgYRj+Oj64tyTgO4iQIDmYXDBqvSWQ/FA4OSCsXOStlF+noU0/NA==",
      "dev": true,
      "peerDependencies": {
        "eslint": ">=7"
      }
    },
    "node_modules/eslint-scope": {
      "version": "7.2.2",
      "resolved": "https://registry.npmjs.org/eslint-scope/-/eslint-scope-7.2.2.tgz",
      "integrity": "sha512-dOt21O7lTMhDM+X9mB4GX+DZrZtCUJPL/wlcTqxyrx5IvO0IYtILdtrQGQp+8n5S0gwSVmOf9NQrjMOgfQZlIg==",
      "dev": true,
      "dependencies": {
        "esrecurse": "^4.3.0",
        "estraverse": "^5.2.0"
      },
      "engines": {
        "node": "^12.22.0 || ^14.17.0 || >=16.0.0"
      },
      "funding": {
        "url": "https://opencollective.com/eslint"
      }
    },
    "node_modules/eslint-visitor-keys": {
      "version": "3.4.3",
      "resolved": "https://registry.npmjs.org/eslint-visitor-keys/-/eslint-visitor-keys-3.4.3.tgz",
      "integrity": "sha512-wpc+LXeiyiisxPlEkUzU6svyS1frIO3Mgxj1fdy7Pm8Ygzguax2N3Fa/D/ag1WqbOprdI+uY6wMUl8/a2G+iag==",
      "dev": true,
      "engines": {
        "node": "^12.22.0 || ^14.17.0 || >=16.0.0"
      },
      "funding": {
        "url": "https://opencollective.com/eslint"
      }
    },
    "node_modules/eslint/node_modules/brace-expansion": {
      "version": "1.1.11",
      "resolved": "https://registry.npmjs.org/brace-expansion/-/brace-expansion-1.1.11.tgz",
      "integrity": "sha512-iCuPHDFgrHX7H2vEI/5xpz07zSHB00TpugqhmYtVmMO6518mCuRMoOYFldEBl0g187ufozdaHgWKcYFb61qGiA==",
      "dev": true,
      "dependencies": {
        "balanced-match": "^1.0.0",
        "concat-map": "0.0.1"
      }
    },
    "node_modules/eslint/node_modules/globals": {
      "version": "13.24.0",
      "resolved": "https://registry.npmjs.org/globals/-/globals-13.24.0.tgz",
      "integrity": "sha512-AhO5QUcj8llrbG09iWhPU2B204J1xnPeL8kQmVorSsy+Sjj1sk8gIyh6cUocGmH4L0UuhAJy+hJMRA4mgA4mFQ==",
      "dev": true,
      "dependencies": {
        "type-fest": "^0.20.2"
      },
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/eslint/node_modules/minimatch": {
      "version": "3.1.2",
      "resolved": "https://registry.npmjs.org/minimatch/-/minimatch-3.1.2.tgz",
      "integrity": "sha512-J7p63hRiAjw1NDEww1W7i37+ByIrOWO5XQQAzZ3VOcL0PNybwpfmV/N05zFAzwQ9USyEcX6t3UO+K5aqBQOIHw==",
      "dev": true,
      "dependencies": {
        "brace-expansion": "^1.1.7"
      },
      "engines": {
        "node": "*"
      }
    },
    "node_modules/espree": {
      "version": "9.6.1",
      "resolved": "https://registry.npmjs.org/espree/-/espree-9.6.1.tgz",
      "integrity": "sha512-oruZaFkjorTpF32kDSI5/75ViwGeZginGGy2NoOSg3Q9bnwlnmDm4HLnkl0RE3n+njDXR037aY1+x58Z/zFdwQ==",
      "dev": true,
      "dependencies": {
        "acorn": "^8.9.0",
        "acorn-jsx": "^5.3.2",
        "eslint-visitor-keys": "^3.4.1"
      },
      "engines": {
        "node": "^12.22.0 || ^14.17.0 || >=16.0.0"
      },
      "funding": {
        "url": "https://opencollective.com/eslint"
      }
    },
    "node_modules/esquery": {
      "version": "1.6.0",
      "resolved": "https://registry.npmjs.org/esquery/-/esquery-1.6.0.tgz",
      "integrity": "sha512-ca9pw9fomFcKPvFLXhBKUK90ZvGibiGOvRJNbjljY7s7uq/5YO4BOzcYtJqExdx99rF6aAcnRxHmcUHcz6sQsg==",
      "dev": true,
      "dependencies": {
        "estraverse": "^5.1.0"
      },
      "engines": {
        "node": ">=0.10"
      }
    },
    "node_modules/esrecurse": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/esrecurse/-/esrecurse-4.3.0.tgz",
      "integrity": "sha512-KmfKL3b6G+RXvP8N1vr3Tq1kL/oCFgn2NYXEtqP8/L3pKapUA4G8cFVaoF3SU323CD4XypR/ffioHmkti6/Tag==",
      "dev": true,
      "dependencies": {
        "estraverse": "^5.2.0"
      },
      "engines": {
        "node": ">=4.0"
      }
    },
    "node_modules/estraverse": {
      "version": "5.3.0",
      "resolved": "https://registry.npmjs.org/estraverse/-/estraverse-5.3.0.tgz",
      "integrity": "sha512-MMdARuVEQziNTeJD8DgMqmhwR11BRQ/cBP+pLtYdSTnf3MIO8fFeiINEbX36ZdNlfU/7A9f3gUw49B3oQsvwBA==",
      "dev": true,
      "engines": {
        "node": ">=4.0"
      }
    },
    "node_modules/esutils": {
      "version": "2.0.3",
      "resolved": "https://registry.npmjs.org/esutils/-/esutils-2.0.3.tgz",
      "integrity": "sha512-kVscqXk4OCp68SZ0dkgEKVi6/8ij300KBWTJq32P/dYeWTSwK41WyTxalN1eRmA5Z9UU/LX9D7FWSmV9SAYx6g==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/eth-block-tracker": {
      "version": "7.1.0",
      "resolved": "https://registry.npmjs.org/eth-block-tracker/-/eth-block-tracker-7.1.0.tgz",
      "integrity": "sha512-8YdplnuE1IK4xfqpf4iU7oBxnOYAc35934o083G8ao+8WM8QQtt/mVlAY6yIAdY1eMeLqg4Z//PZjJGmWGPMRg==",
      "dependencies": {
        "@metamask/eth-json-rpc-provider": "^1.0.0",
        "@metamask/safe-event-emitter": "^3.0.0",
        "@metamask/utils": "^5.0.1",
        "json-rpc-random-id": "^1.0.1",
        "pify": "^3.0.0"
      },
      "engines": {
        "node": ">=14.0.0"
      }
    },
    "node_modules/eth-json-rpc-filters": {
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/eth-json-rpc-filters/-/eth-json-rpc-filters-6.0.1.tgz",
      "integrity": "sha512-ITJTvqoCw6OVMLs7pI8f4gG92n/St6x80ACtHodeS+IXmO0w+t1T5OOzfSt7KLSMLRkVUoexV7tztLgDxg+iig==",
      "dependencies": {
        "@metamask/safe-event-emitter": "^3.0.0",
        "async-mutex": "^0.2.6",
        "eth-query": "^2.1.2",
        "json-rpc-engine": "^6.1.0",
        "pify": "^5.0.0"
      },
      "engines": {
        "node": ">=14.0.0"
      }
    },
    "node_modules/eth-json-rpc-filters/node_modules/pify": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/pify/-/pify-5.0.0.tgz",
      "integrity": "sha512-eW/gHNMlxdSP6dmG6uJip6FXN0EQBwm2clYYd8Wul42Cwu/DK8HEftzsapcNdYe2MfLiIwZqsDk2RDEsTE79hA==",
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/eth-query": {
      "version": "2.1.2",
      "resolved": "https://registry.npmjs.org/eth-query/-/eth-query-2.1.2.tgz",
      "integrity": "sha512-srES0ZcvwkR/wd5OQBRA1bIJMww1skfGS0s8wlwK3/oNP4+wnds60krvu5R1QbpRQjMmpG5OMIWro5s7gvDPsA==",
      "dependencies": {
        "json-rpc-random-id": "^1.0.0",
        "xtend": "^4.0.1"
      }
    },
    "node_modules/eth-rpc-errors": {
      "version": "4.0.3",
      "resolved": "https://registry.npmjs.org/eth-rpc-errors/-/eth-rpc-errors-4.0.3.tgz",
      "integrity": "sha512-Z3ymjopaoft7JDoxZcEb3pwdGh7yiYMhOwm2doUt6ASXlMavpNlK6Cre0+IMl2VSGyEU9rkiperQhp5iRxn5Pg==",
      "dependencies": {
        "fast-safe-stringify": "^2.0.6"
      }
    },
    "node_modules/ethereum-cryptography": {
      "version": "2.2.1",
      "resolved": "https://registry.npmjs.org/ethereum-cryptography/-/ethereum-cryptography-2.2.1.tgz",
      "integrity": "sha512-r/W8lkHSiTLxUxW8Rf3u4HGB0xQweG2RyETjywylKZSzLWoWAijRz8WCuOtJ6wah+avllXBqZuk29HCCvhEIRg==",
      "dependencies": {
        "@noble/curves": "1.4.2",
        "@noble/hashes": "1.4.0",
        "@scure/bip32": "1.4.0",
        "@scure/bip39": "1.3.0"
      }
    },
    "node_modules/ethereum-cryptography/node_modules/@noble/curves": {
      "version": "1.4.2",
      "resolved": "https://registry.npmjs.org/@noble/curves/-/curves-1.4.2.tgz",
      "integrity": "sha512-TavHr8qycMChk8UwMld0ZDRvatedkzWfH8IiaeGCfymOP5i0hSCozz9vHOL0nkwk7HRMlFnAiKpS2jrUmSybcw==",
      "dependencies": {
        "@noble/hashes": "1.4.0"
      },
      "funding": {
        "url": "https://paulmillr.com/funding/"
      }
    },
    "node_modules/ethereum-cryptography/node_modules/@noble/hashes": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/@noble/hashes/-/hashes-1.4.0.tgz",
      "integrity": "sha512-V1JJ1WTRUqHHrOSh597hURcMqVKVGL/ea3kv0gSnEdsEZ0/+VyPghM1lMNGc00z7CIQorSvbKpuJkxvuHbvdbg==",
      "engines": {
        "node": ">= 16"
      },
      "funding": {
        "url": "https://paulmillr.com/funding/"
      }
    },
    "node_modules/ethjs-unit": {
      "version": "0.1.6",
      "resolved": "https://registry.npmjs.org/ethjs-unit/-/ethjs-unit-0.1.6.tgz",
      "integrity": "sha512-/Sn9Y0oKl0uqQuvgFk/zQgR7aw1g36qX/jzSQ5lSwlO0GigPymk4eGQfeNTD03w1dPOqfz8V77Cy43jH56pagw==",
      "dependencies": {
        "bn.js": "4.11.6",
        "number-to-bn": "1.7.0"
      },
      "engines": {
        "node": ">=6.5.0",
        "npm": ">=3"
      }
    },
    "node_modules/ethjs-unit/node_modules/bn.js": {
      "version": "4.11.6",
      "resolved": "https://registry.npmjs.org/bn.js/-/bn.js-4.11.6.tgz",
      "integrity": "sha512-XWwnNNFCuuSQ0m3r3C4LE3EiORltHd9M05pq6FOlVeiophzRbMo50Sbz1ehl8K3Z+jw9+vmgnXefY1hz8X+2wA=="
    },
    "node_modules/ev-emitter": {
      "version": "2.1.2",
      "resolved": "https://registry.npmjs.org/ev-emitter/-/ev-emitter-2.1.2.tgz",
      "integrity": "sha512-jQ5Ql18hdCQ4qS+RCrbLfz1n+Pags27q5TwMKvZyhp5hh2UULUYZUy1keqj6k6SYsdqIYjnmz7xyyEY0V67B8Q=="
    },
    "node_modules/event-stream": {
      "version": "3.3.4",
      "resolved": "https://registry.npmjs.org/event-stream/-/event-stream-3.3.4.tgz",
      "integrity": "sha512-QHpkERcGsR0T7Qm3HNJSyXKEEj8AHNxkY3PK8TS2KJvQ7NiSHe3DDpwVKKtoYprL/AreyzFBeIkBIWChAqn60g==",
      "dependencies": {
        "duplexer": "~0.1.1",
        "from": "~0",
        "map-stream": "~0.1.0",
        "pause-stream": "0.0.11",
        "split": "0.3",
        "stream-combiner": "~0.0.4",
        "through": "~2.3.1"
      }
    },
    "node_modules/event-target-shim": {
      "version": "5.0.1",
      "resolved": "https://registry.npmjs.org/event-target-shim/-/event-target-shim-5.0.1.tgz",
      "integrity": "sha512-i/2XbnSz/uxRCU6+NdVJgKWDTM427+MqYbkQzD321DuCQJUqOuJKIA0IM2+W2xtYHdKOmZ4dR6fExsd4SXL+WQ==",
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/eventemitter3": {
      "version": "4.0.7",
      "resolved": "https://registry.npmjs.org/eventemitter3/-/eventemitter3-4.0.7.tgz",
      "integrity": "sha512-8guHBZCwKnFhYdHr2ysuRWErTwhoN2X8XELRlrRwpmfeY2jjuUN4taQMsULKUVo1K4DvZl+0pgfyoysHxvmvEw=="
    },
    "node_modules/events": {
      "version": "3.3.0",
      "resolved": "https://registry.npmjs.org/events/-/events-3.3.0.tgz",
      "integrity": "sha512-mQw+2fkQbALzQ7V0MY0IqdnXNOeTtP4r0lN9z7AAawCXgqea7bDii20AYrIBrFd/Hx0M2Ocz6S111CaFkUcb0Q==",
      "engines": {
        "node": ">=0.8.x"
      }
    },
    "node_modules/execa": {
      "version": "8.0.1",
      "resolved": "https://registry.npmjs.org/execa/-/execa-8.0.1.tgz",
      "integrity": "sha512-VyhnebXciFV2DESc+p6B+y0LjSm0krU4OgJN44qFAhBY0TJ+1V61tYD2+wHusZ6F9n5K+vl8k0sTy7PEfV4qpg==",
      "dependencies": {
        "cross-spawn": "^7.0.3",
        "get-stream": "^8.0.1",
        "human-signals": "^5.0.0",
        "is-stream": "^3.0.0",
        "merge-stream": "^2.0.0",
        "npm-run-path": "^5.1.0",
        "onetime": "^6.0.0",
        "signal-exit": "^4.1.0",
        "strip-final-newline": "^3.0.0"
      },
      "engines": {
        "node": ">=16.17"
      },
      "funding": {
        "url": "https://github.com/sindresorhus/execa?sponsor=1"
      }
    },
    "node_modules/eyes": {
      "version": "0.1.8",
      "resolved": "https://registry.npmjs.org/eyes/-/eyes-0.1.8.tgz",
      "integrity": "sha512-GipyPsXO1anza0AOZdy69Im7hGFCNB7Y/NGjDlZGJ3GJJLtwNSb2vrzYrTYJRrRloVx7pl+bhUaTB8yiccPvFQ==",
      "engines": {
        "node": "> 0.1.90"
      }
    },
    "node_modules/fast-deep-equal": {
      "version": "3.1.3",
      "resolved": "https://registry.npmjs.org/fast-deep-equal/-/fast-deep-equal-3.1.3.tgz",
      "integrity": "sha512-f3qQ9oQy9j2AhBe/H9VC91wLmKBCCU/gDOnKNAYG5hswO7BLKj09Hc5HYNz9cGI++xlpDCIgDaitVs03ATR84Q==",
      "dev": true
    },
    "node_modules/fast-glob": {
      "version": "3.3.2",
      "resolved": "https://registry.npmjs.org/fast-glob/-/fast-glob-3.3.2.tgz",
      "integrity": "sha512-oX2ruAFQwf/Orj8m737Y5adxDQO0LAB7/S5MnxCdTNDd4p6BsyIVsv9JQsATbTSq8KHRpLwIHbVlUNatxd+1Ow==",
      "dev": true,
      "dependencies": {
        "@nodelib/fs.stat": "^2.0.2",
        "@nodelib/fs.walk": "^1.2.3",
        "glob-parent": "^5.1.2",
        "merge2": "^1.3.0",
        "micromatch": "^4.0.4"
      },
      "engines": {
        "node": ">=8.6.0"
      }
    },
    "node_modules/fast-glob/node_modules/glob-parent": {
      "version": "5.1.2",
      "resolved": "https://registry.npmjs.org/glob-parent/-/glob-parent-5.1.2.tgz",
      "integrity": "sha512-AOIgSQCepiJYwP3ARnGx+5VnTu2HBYdzbGP45eLw1vr3zB3vZLeyed1sC9hnbcOc9/SrMyM5RPQrkGz4aS9Zow==",
      "dev": true,
      "dependencies": {
        "is-glob": "^4.0.1"
      },
      "engines": {
        "node": ">= 6"
      }
    },
    "node_modules/fast-json-stable-stringify": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/fast-json-stable-stringify/-/fast-json-stable-stringify-2.1.0.tgz",
      "integrity": "sha512-lhd/wF+Lk98HZoTCtlVraHtfh5XYijIjalXck7saUtuanSDyLMxnHhSXEDJqHxD7msR8D0uCmqlkwjCV8xvwHw=="
    },
    "node_modules/fast-levenshtein": {
      "version": "2.0.6",
      "resolved": "https://registry.npmjs.org/fast-levenshtein/-/fast-levenshtein-2.0.6.tgz",
      "integrity": "sha512-DCXu6Ifhqcks7TZKY3Hxp3y6qphY5SJZmrWMDrKcERSOXWQdMhU9Ig/PYrzyw/ul9jOIyh0N4M0tbC5hodg8dw==",
      "dev": true
    },
    "node_modules/fast-redact": {
      "version": "3.5.0",
      "resolved": "https://registry.npmjs.org/fast-redact/-/fast-redact-3.5.0.tgz",
      "integrity": "sha512-dwsoQlS7h9hMeYUq1W++23NDcBLV4KqONnITDV9DjfS3q1SgDGVrBdvvTLUotWtPSD7asWDV9/CmsZPy8Hf70A==",
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/fast-safe-stringify": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/fast-safe-stringify/-/fast-safe-stringify-2.1.1.tgz",
      "integrity": "sha512-W+KJc2dmILlPplD/H4K9l9LcAHAfPtP6BY84uVLXQ6Evcz9Lcg33Y2z1IVblT6xdY54PXYVHEv+0Wpq8Io6zkA=="
    },
    "node_modules/fast-stable-stringify": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/fast-stable-stringify/-/fast-stable-stringify-1.0.0.tgz",
      "integrity": "sha512-wpYMUmFu5f00Sm0cj2pfivpmawLZ0NKdviQ4w9zJeR8JVtOpOxHmLaJuj0vxvGqMJQWyP/COUkF75/57OKyRag=="
    },
    "node_modules/fast-xml-parser": {
      "version": "4.4.1",
      "resolved": "https://registry.npmjs.org/fast-xml-parser/-/fast-xml-parser-4.4.1.tgz",
      "integrity": "sha512-xkjOecfnKGkSsOwtZ5Pz7Us/T6mrbPQrq0nh+aCO5V9nk5NLWmasAHumTKjiPJPWANe+kAZ84Jc8ooJkzZ88Sw==",
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/NaturalIntelligence"
        },
        {
          "type": "paypal",
          "url": "https://paypal.me/naturalintelligence"
        }
      ],
      "dependencies": {
        "strnum": "^1.0.5"
      },
      "bin": {
        "fxparser": "src/cli/cli.js"
      }
    },
    "node_modules/fastparse": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/fastparse/-/fastparse-1.1.2.tgz",
      "integrity": "sha512-483XLLxTVIwWK3QTrMGRqUfUpoOs/0hbQrl2oz4J0pAcm3A3bu84wxTFqGqkJzewCLdME38xJLJAxBABfQT8sQ==",
      "dev": true
    },
    "node_modules/fastq": {
      "version": "1.17.1",
      "resolved": "https://registry.npmjs.org/fastq/-/fastq-1.17.1.tgz",
      "integrity": "sha512-sRVD3lWVIXWg6By68ZN7vho9a1pQcN/WBFaAAsDDFzlJjvoGx0P8z7V1t72grFJfJhu3YPZBuu25f7Kaw2jN1w==",
      "dev": true,
      "dependencies": {
        "reusify": "^1.0.4"
      }
    },
    "node_modules/file-entry-cache": {
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/file-entry-cache/-/file-entry-cache-6.0.1.tgz",
      "integrity": "sha512-7Gps/XWymbLk2QLYK4NzpMOrYjMhdIxXuIvy2QBsLE6ljuodKvdkWs/cpyJJ3CVIVpH0Oi1Hvg1ovbMzLdFBBg==",
      "dev": true,
      "dependencies": {
        "flat-cache": "^3.0.4"
      },
      "engines": {
        "node": "^10.12.0 || >=12.0.0"
      }
    },
    "node_modules/file-uri-to-path": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/file-uri-to-path/-/file-uri-to-path-1.0.0.tgz",
      "integrity": "sha512-0Zt+s3L7Vf1biwWZ29aARiVYLx7iMGnEUl9x33fbB/j3jR81u/O2LbqK+Bm1CDSNDKVtJ/YjwY7TUd5SkeLQLw=="
    },
    "node_modules/fill-range": {
      "version": "7.1.1",
      "resolved": "https://registry.npmjs.org/fill-range/-/fill-range-7.1.1.tgz",
      "integrity": "sha512-YsGpe3WHLK8ZYi4tWDg2Jy3ebRz2rXowDxnld4bkQB00cc/1Zw9AWnC0i9ztDJitivtQvaI9KaLyKrc+hBW0yg==",
      "dependencies": {
        "to-regex-range": "^5.0.1"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/filter-obj": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/filter-obj/-/filter-obj-1.1.0.tgz",
      "integrity": "sha512-8rXg1ZnX7xzy2NGDVkBVaAy+lSlPNwad13BtgSlLuxfIslyt5Vg64U7tFcCt4WS1R0hvtnQybT/IyCkGZ3DpXQ==",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/find-up": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/find-up/-/find-up-5.0.0.tgz",
      "integrity": "sha512-78/PXT1wlLLDgTzDs7sjq9hzz0vXD+zn+7wypEe4fXQxCmdmqfGsEPQxmiCSQI3ajFV91bVSsvNtrJRiW6nGng==",
      "dev": true,
      "dependencies": {
        "locate-path": "^6.0.0",
        "path-exists": "^4.0.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/flat-cache": {
      "version": "3.2.0",
      "resolved": "https://registry.npmjs.org/flat-cache/-/flat-cache-3.2.0.tgz",
      "integrity": "sha512-CYcENa+FtcUKLmhhqyctpclsq7QF38pKjZHsGNiSQF5r4FtoKDWabFDl3hzaEQMvT1LHEysw5twgLvpYYb4vbw==",
      "dev": true,
      "dependencies": {
        "flatted": "^3.2.9",
        "keyv": "^4.5.3",
        "rimraf": "^3.0.2"
      },
      "engines": {
        "node": "^10.12.0 || >=12.0.0"
      }
    },
    "node_modules/flatted": {
      "version": "3.3.1",
      "resolved": "https://registry.npmjs.org/flatted/-/flatted-3.3.1.tgz",
      "integrity": "sha512-X8cqMLLie7KsNUDSdzeN8FYK9rEt4Dt67OsG/DNGnYTSDBG4uFAJFBnUeiV+zCVAvwFy56IjM9sH51jVaEhNxw==",
      "dev": true
    },
    "node_modules/follow-redirects": {
      "version": "1.15.9",
      "resolved": "https://registry.npmjs.org/follow-redirects/-/follow-redirects-1.15.9.tgz",
      "integrity": "sha512-gew4GsXizNgdoRyqmyfMHyAmXsZDk6mHkSxZFCzW9gwlbtOW44CDtYavM+y+72qD/Vq2l550kMF52DT8fOLJqQ==",
      "funding": [
        {
          "type": "individual",
          "url": "https://github.com/sponsors/RubenVerborgh"
        }
      ],
      "engines": {
        "node": ">=4.0"
      },
      "peerDependenciesMeta": {
        "debug": {
          "optional": true
        }
      }
    },
    "node_modules/foreground-child": {
      "version": "3.3.0",
      "resolved": "https://registry.npmjs.org/foreground-child/-/foreground-child-3.3.0.tgz",
      "integrity": "sha512-Ld2g8rrAyMYFXBhEqMz8ZAHBi4J4uS1i/CxGMDnjyFWddMXLVcDp051DZfu+t7+ab7Wv6SMqpWmyFIj5UbfFvg==",
      "dev": true,
      "dependencies": {
        "cross-spawn": "^7.0.0",
        "signal-exit": "^4.0.1"
      },
      "engines": {
        "node": ">=14"
      },
      "funding": {
        "url": "https://github.com/sponsors/isaacs"
      }
    },
    "node_modules/form-data": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/form-data/-/form-data-4.0.1.tgz",
      "integrity": "sha512-tzN8e4TX8+kkxGPK8D5u0FNmjPUjw3lwC9lSLxxoB/+GtsJG91CO8bSWy73APlgAZzZbXEYZJuxjkHH2w+Ezhw==",
      "dependencies": {
        "asynckit": "^0.4.0",
        "combined-stream": "^1.0.8",
        "mime-types": "^2.1.12"
      },
      "engines": {
        "node": ">= 6"
      }
    },
    "node_modules/fraction.js": {
      "version": "4.3.7",
      "resolved": "https://registry.npmjs.org/fraction.js/-/fraction.js-4.3.7.tgz",
      "integrity": "sha512-ZsDfxO51wGAXREY55a7la9LScWpwv9RxIrYABrlvOFBlH/ShPnrtsXeuUIfXKKOVicNxQ+o8JTbJvjS4M89yew==",
      "dev": true,
      "engines": {
        "node": "*"
      },
      "funding": {
        "type": "patreon",
        "url": "https://github.com/sponsors/rawify"
      }
    },
    "node_modules/from": {
      "version": "0.1.7",
      "resolved": "https://registry.npmjs.org/from/-/from-0.1.7.tgz",
      "integrity": "sha512-twe20eF1OxVxp/ML/kq2p1uc6KvFK/+vs8WjEbeKmV2He22MKm7YF2ANIt+EOqhJ5L3K/SuuPhk0hWQDjOM23g=="
    },
    "node_modules/fs.realpath": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/fs.realpath/-/fs.realpath-1.0.0.tgz",
      "integrity": "sha512-OO0pH2lK6a0hZnAdau5ItzHPI6pUlvI7jMVnxUQRtw4owF2wk8lOSabtGDCTP4Ggrg2MbGnWO9X8K1t4+fGMDw==",
      "dev": true
    },
    "node_modules/fsevents": {
      "version": "2.3.3",
      "resolved": "https://registry.npmjs.org/fsevents/-/fsevents-2.3.3.tgz",
      "integrity": "sha512-5xoDfX+fL7faATnagmWPpbFtwh/R77WmMMqqHGS65C3vvB0YHrgF+B1YmZ3441tMj5n63k0212XNoJwzlhffQw==",
      "hasInstallScript": true,
      "optional": true,
      "os": [
        "darwin"
      ],
      "engines": {
        "node": "^8.16.0 || ^10.6.0 || >=11.0.0"
      }
    },
    "node_modules/function-bind": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/function-bind/-/function-bind-1.1.2.tgz",
      "integrity": "sha512-7XHNxH7qX9xG5mIwxkhumTox/MIRNcOgDrxWsMt2pAr23WHp6MrRlN7FBSFpCpr+oVO0F744iUgR82nJMfG2SA==",
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/gensync": {
      "version": "1.0.0-beta.2",
      "resolved": "https://registry.npmjs.org/gensync/-/gensync-1.0.0-beta.2.tgz",
      "integrity": "sha512-3hN7NaskYvMDLQY55gnW3NQ+mesEAepTqlg+VEbj7zzqEMBVNhzcGYYeqFo/TlYz6eQiFcp1HcsCZO+nGgS8zg==",
      "dev": true,
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/get-caller-file": {
      "version": "2.0.5",
      "resolved": "https://registry.npmjs.org/get-caller-file/-/get-caller-file-2.0.5.tgz",
      "integrity": "sha512-DyFP3BM/3YHTQOCUL/w0OZHR0lpKeGrxotcHWcqNEdnltqFwXVfhEBQ94eIo34AfQpo0rGki4cyIiftY06h2Fg==",
      "engines": {
        "node": "6.* || 8.* || >= 10.*"
      }
    },
    "node_modules/get-intrinsic": {
      "version": "1.2.4",
      "resolved": "https://registry.npmjs.org/get-intrinsic/-/get-intrinsic-1.2.4.tgz",
      "integrity": "sha512-5uYhsJH8VJBTv7oslg4BznJYhDoRI6waYCxMmCdnTrcCrHA/fCFKoTFz2JKKE0HdDFUF7/oQuhzumXJK7paBRQ==",
      "dependencies": {
        "es-errors": "^1.3.0",
        "function-bind": "^1.1.2",
        "has-proto": "^1.0.1",
        "has-symbols": "^1.0.3",
        "hasown": "^2.0.0"
      },
      "engines": {
        "node": ">= 0.4"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/get-port-please": {
      "version": "3.1.2",
      "resolved": "https://registry.npmjs.org/get-port-please/-/get-port-please-3.1.2.tgz",
      "integrity": "sha512-Gxc29eLs1fbn6LQ4jSU4vXjlwyZhF5HsGuMAa7gqBP4Rw4yxxltyDUuF5MBclFzDTXO+ACchGQoeela4DSfzdQ=="
    },
    "node_modules/get-size": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/get-size/-/get-size-3.0.0.tgz",
      "integrity": "sha512-Y8aiXLq4leR7807UY0yuKEwif5s3kbVp1nTv+i4jBeoUzByTLKkLWu/HorS6/pB+7gsB0o7OTogC8AoOOeT0Hw=="
    },
    "node_modules/get-stream": {
      "version": "8.0.1",
      "resolved": "https://registry.npmjs.org/get-stream/-/get-stream-8.0.1.tgz",
      "integrity": "sha512-VaUJspBffn/LMCJVoMvSAdmscJyS1auj5Zulnn5UoYcY531UWmdwhRWkcGKnGU93m5HSXP9LP2usOryrBtQowA==",
      "engines": {
        "node": ">=16"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/glob": {
      "version": "7.2.3",
      "resolved": "https://registry.npmjs.org/glob/-/glob-7.2.3.tgz",
      "integrity": "sha512-nFR0zLpU2YCaRxwoCJvL6UvCH2JFyFVIvwTLsIf21AuHlMskA1hhTdk+LlYJtOlYt9v6dvszD2BGRqBL+iQK9Q==",
      "deprecated": "Glob versions prior to v9 are no longer supported",
      "dev": true,
      "dependencies": {
        "fs.realpath": "^1.0.0",
        "inflight": "^1.0.4",
        "inherits": "2",
        "minimatch": "^3.1.1",
        "once": "^1.3.0",
        "path-is-absolute": "^1.0.0"
      },
      "engines": {
        "node": "*"
      },
      "funding": {
        "url": "https://github.com/sponsors/isaacs"
      }
    },
    "node_modules/glob-parent": {
      "version": "6.0.2",
      "resolved": "https://registry.npmjs.org/glob-parent/-/glob-parent-6.0.2.tgz",
      "integrity": "sha512-XxwI8EOhVQgWp6iDL+3b0r86f4d6AX6zSU55HfB4ydCEuXLXc5FcYeOu+nnGftS4TEju/11rt4KJPTMgbfmv4A==",
      "dev": true,
      "dependencies": {
        "is-glob": "^4.0.3"
      },
      "engines": {
        "node": ">=10.13.0"
      }
    },
    "node_modules/glob/node_modules/brace-expansion": {
      "version": "1.1.11",
      "resolved": "https://registry.npmjs.org/brace-expansion/-/brace-expansion-1.1.11.tgz",
      "integrity": "sha512-iCuPHDFgrHX7H2vEI/5xpz07zSHB00TpugqhmYtVmMO6518mCuRMoOYFldEBl0g187ufozdaHgWKcYFb61qGiA==",
      "dev": true,
      "dependencies": {
        "balanced-match": "^1.0.0",
        "concat-map": "0.0.1"
      }
    },
    "node_modules/glob/node_modules/minimatch": {
      "version": "3.1.2",
      "resolved": "https://registry.npmjs.org/minimatch/-/minimatch-3.1.2.tgz",
      "integrity": "sha512-J7p63hRiAjw1NDEww1W7i37+ByIrOWO5XQQAzZ3VOcL0PNybwpfmV/N05zFAzwQ9USyEcX6t3UO+K5aqBQOIHw==",
      "dev": true,
      "dependencies": {
        "brace-expansion": "^1.1.7"
      },
      "engines": {
        "node": "*"
      }
    },
    "node_modules/globals": {
      "version": "11.12.0",
      "resolved": "https://registry.npmjs.org/globals/-/globals-11.12.0.tgz",
      "integrity": "sha512-WOBp/EEGUiIsJSp7wcv/y6MO+lV9UoncWqxuFfm8eBwzWNgyfBd6Gz+IeKQ9jCmyhoH99g15M3T+QaVHFjizVA==",
      "dev": true,
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/globby": {
      "version": "11.1.0",
      "resolved": "https://registry.npmjs.org/globby/-/globby-11.1.0.tgz",
      "integrity": "sha512-jhIXaOzy1sb8IyocaruWSn1TjmnBVs8Ayhcy83rmxNJ8q2uWKCAj3CnJY+KpGSXCueAPc0i05kVvVKtP1t9S3g==",
      "dev": true,
      "dependencies": {
        "array-union": "^2.1.0",
        "dir-glob": "^3.0.1",
        "fast-glob": "^3.2.9",
        "ignore": "^5.2.0",
        "merge2": "^1.4.1",
        "slash": "^3.0.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/gopd": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/gopd/-/gopd-1.0.1.tgz",
      "integrity": "sha512-d65bNlIadxvpb/A2abVdlqKqV563juRnZ1Wtk6s1sIR8uNsXR70xqIzVqxVf1eTqDunwT2MkczEeaezCKTZhwA==",
      "dependencies": {
        "get-intrinsic": "^1.1.3"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/graphemer": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/graphemer/-/graphemer-1.4.0.tgz",
      "integrity": "sha512-EtKwoO6kxCL9WO5xipiHTZlSzBm7WLT627TqC/uVRd0HKmq8NXyebnNYxDoBi7wt8eTWrUrKXCOVaFq9x1kgag==",
      "dev": true
    },
    "node_modules/h3": {
      "version": "1.13.0",
      "resolved": "https://registry.npmjs.org/h3/-/h3-1.13.0.tgz",
      "integrity": "sha512-vFEAu/yf8UMUcB4s43OaDaigcqpQd14yanmOsn+NcRX3/guSKncyE2rOYhq8RIchgJrPSs/QiIddnTTR1ddiAg==",
      "dependencies": {
        "cookie-es": "^1.2.2",
        "crossws": ">=0.2.0 <0.4.0",
        "defu": "^6.1.4",
        "destr": "^2.0.3",
        "iron-webcrypto": "^1.2.1",
        "ohash": "^1.1.4",
        "radix3": "^1.1.2",
        "ufo": "^1.5.4",
        "uncrypto": "^0.1.3",
        "unenv": "^1.10.0"
      }
    },
    "node_modules/has-flag": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-4.0.0.tgz",
      "integrity": "sha512-EykJT/Q1KjTWctppgIAgfSO0tKVuZUjhgMr17kqTumMl6Afv3EISleU7qZUzoXDFTAHTDC4NOoG/ZxU3EvlMPQ==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/has-property-descriptors": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/has-property-descriptors/-/has-property-descriptors-1.0.2.tgz",
      "integrity": "sha512-55JNKuIW+vq4Ke1BjOTjM2YctQIvCT7GFzHwmfZPGo5wnrgkid0YQtnAleFSqumZm4az3n2BS+erby5ipJdgrg==",
      "dependencies": {
        "es-define-property": "^1.0.0"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/has-proto": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/has-proto/-/has-proto-1.0.3.tgz",
      "integrity": "sha512-SJ1amZAJUiZS+PhsVLf5tGydlaVB8EdFpaSO4gmiUKUOxk8qzn5AIy4ZeJUmh22znIdk/uMAUT2pl3FxzVUH+Q==",
      "engines": {
        "node": ">= 0.4"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/has-symbols": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/has-symbols/-/has-symbols-1.0.3.tgz",
      "integrity": "sha512-l3LCuF6MgDNwTDKkdYGEihYjt5pRPbEg46rtlmnSPlUbgmB8LOIrKJbYYFBSbnPaJexMKtiPO8hmeRjRz2Td+A==",
      "engines": {
        "node": ">= 0.4"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/hash.js": {
      "version": "1.1.7",
      "resolved": "https://registry.npmjs.org/hash.js/-/hash.js-1.1.7.tgz",
      "integrity": "sha512-taOaskGt4z4SOANNseOviYDvjEJinIkRgmp7LbKP2YTTmVxWBl87s/uzK9r+44BclBSp2X7K1hqeNfz9JbBeXA==",
      "dependencies": {
        "inherits": "^2.0.3",
        "minimalistic-assert": "^1.0.1"
      }
    },
    "node_modules/hasown": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/hasown/-/hasown-2.0.2.tgz",
      "integrity": "sha512-0hJU9SCPvmMzIBdZFqNPXWa6dqh7WdH0cII9y+CyS8rG3nL48Bclra9HmKhVVUHyPWNH5Y7xDwAB7bfgSjkUMQ==",
      "dependencies": {
        "function-bind": "^1.1.2"
      },
      "engines": {
        "node": ">= 0.4"
      }
    },
    "node_modules/hey-listen": {
      "version": "1.0.8",
      "resolved": "https://registry.npmjs.org/hey-listen/-/hey-listen-1.0.8.tgz",
      "integrity": "sha512-COpmrF2NOg4TBWUJ5UVyaCU2A88wEMkUPK4hNqyCkqHbxT92BbvfjoSozkAIIm6XhicGlJHhFdullInrdhwU8Q=="
    },
    "node_modules/hmac-drbg": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/hmac-drbg/-/hmac-drbg-1.0.1.tgz",
      "integrity": "sha512-Tti3gMqLdZfhOQY1Mzf/AanLiqh1WTiJgEj26ZuYQ9fbkLomzGchCws4FyrSd4VkpBfiNhaE1On+lOz894jvXg==",
      "dependencies": {
        "hash.js": "^1.0.3",
        "minimalistic-assert": "^1.0.0",
        "minimalistic-crypto-utils": "^1.0.1"
      }
    },
    "node_modules/html-parse-stringify": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/html-parse-stringify/-/html-parse-stringify-3.0.1.tgz",
      "integrity": "sha512-KknJ50kTInJ7qIScF3jeaFRpMpE8/lfiTdzf/twXyPBLAGrLRTmkz3AdTnKeh40X8k9L2fdYwEp/42WGXIRGcg==",
      "dependencies": {
        "void-elements": "3.1.0"
      }
    },
    "node_modules/http-shutdown": {
      "version": "1.2.2",
      "resolved": "https://registry.npmjs.org/http-shutdown/-/http-shutdown-1.2.2.tgz",
      "integrity": "sha512-S9wWkJ/VSY9/k4qcjG318bqJNruzE4HySUhFYknwmu6LBP97KLLfwNf+n4V1BHurvFNkSKLFnK/RsuUnRTf9Vw==",
      "engines": {
        "iojs": ">= 1.0.0",
        "node": ">= 0.12.0"
      }
    },
    "node_modules/human-signals": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/human-signals/-/human-signals-5.0.0.tgz",
      "integrity": "sha512-AXcZb6vzzrFAUE61HnN4mpLqd/cSIwNQjtNWR0euPm6y0iqx3G4gOXaIDdtdDwZmhwe82LA6+zinmW4UBWVePQ==",
      "engines": {
        "node": ">=16.17.0"
      }
    },
    "node_modules/humanize-ms": {
      "version": "1.2.1",
      "resolved": "https://registry.npmjs.org/humanize-ms/-/humanize-ms-1.2.1.tgz",
      "integrity": "sha512-Fl70vYtsAFb/C06PTS9dZBo7ihau+Tu/DNCk/OyHhea07S+aeMWpFFkUaXRa8fI+ScZbEI8dfSxwY7gxZ9SAVQ==",
      "dependencies": {
        "ms": "^2.0.0"
      }
    },
    "node_modules/humps": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/humps/-/humps-2.0.1.tgz",
      "integrity": "sha512-E0eIbrFWUhwfXJmsbdjRQFQPrl5pTEoKlz163j1mTqqUnU9PgR4AgB8AIITzuB3vLBdxZXyZ9TDIrwB2OASz4g=="
    },
    "node_modules/i18next": {
      "version": "22.5.1",
      "resolved": "https://registry.npmjs.org/i18next/-/i18next-22.5.1.tgz",
      "integrity": "sha512-8TGPgM3pAD+VRsMtUMNknRz3kzqwp/gPALrWMsDnmC1mKqJwpWyooQRLMcbTwq8z8YwSmuj+ZYvc+xCuEpkssA==",
      "funding": [
        {
          "type": "individual",
          "url": "https://locize.com"
        },
        {
          "type": "individual",
          "url": "https://locize.com/i18next.html"
        },
        {
          "type": "individual",
          "url": "https://www.i18next.com/how-to/faq#i18next-is-awesome.-how-can-i-support-the-project"
        }
      ],
      "dependencies": {
        "@babel/runtime": "^7.20.6"
      }
    },
    "node_modules/idb-keyval": {
      "version": "6.2.1",
      "resolved": "https://registry.npmjs.org/idb-keyval/-/idb-keyval-6.2.1.tgz",
      "integrity": "sha512-8Sb3veuYCyrZL+VBt9LJfZjLUPWVvqn8tG28VqYNFCo43KHcKuq+b4EiXGeuaLAQWL2YmyDgMp2aSpH9JHsEQg=="
    },
    "node_modules/ieee754": {
      "version": "1.2.1",
      "resolved": "https://registry.npmjs.org/ieee754/-/ieee754-1.2.1.tgz",
      "integrity": "sha512-dcyqhDvX1C46lXZcVqCpK+FtMRQVdIMN6/Df5js2zouUsqG7I6sFxitIC+7KYK29KdXOLHdu9zL4sFnoVQnqaA==",
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/feross"
        },
        {
          "type": "patreon",
          "url": "https://www.patreon.com/feross"
        },
        {
          "type": "consulting",
          "url": "https://feross.org/support"
        }
      ]
    },
    "node_modules/ignore": {
      "version": "5.3.2",
      "resolved": "https://registry.npmjs.org/ignore/-/ignore-5.3.2.tgz",
      "integrity": "sha512-hsBTNUqQTDwkWtcdYI2i06Y/nUBEsNEDJKjWdigLvegy8kDuJAS8uRlpkkcQpyEXL0Z/pjDy5HBmMjRCJ2gq+g==",
      "dev": true,
      "engines": {
        "node": ">= 4"
      }
    },
    "node_modules/import-fresh": {
      "version": "3.3.0",
      "resolved": "https://registry.npmjs.org/import-fresh/-/import-fresh-3.3.0.tgz",
      "integrity": "sha512-veYYhQa+D1QBKznvhUHxb8faxlrwUnxseDAbAp457E0wLNio2bOSKnjYDhMj+YiAq61xrMGhQk9iXVk5FzgQMw==",
      "dev": true,
      "dependencies": {
        "parent-module": "^1.0.0",
        "resolve-from": "^4.0.0"
      },
      "engines": {
        "node": ">=6"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/imurmurhash": {
      "version": "0.1.4",
      "resolved": "https://registry.npmjs.org/imurmurhash/-/imurmurhash-0.1.4.tgz",
      "integrity": "sha512-JmXMZ6wuvDmLiHEml9ykzqO6lwFbof0GG4IkcGaENdCRDDmMVnny7s5HsIgHCbaq0w2MyPhDqkhTUgS2LU2PHA==",
      "dev": true,
      "engines": {
        "node": ">=0.8.19"
      }
    },
    "node_modules/inflight": {
      "version": "1.0.6",
      "resolved": "https://registry.npmjs.org/inflight/-/inflight-1.0.6.tgz",
      "integrity": "sha512-k92I/b08q4wvFscXCLvqfsHCrjrF7yiXsQuIVvVE7N82W3+aqpzuUdBbfhWcy/FZR3/4IgflMgKLOsvPDrGCJA==",
      "deprecated": "This module is not supported, and leaks memory. Do not use it. Check out lru-cache if you want a good and tested way to coalesce async requests by a key value, which is much more comprehensive and powerful.",
      "dev": true,
      "dependencies": {
        "once": "^1.3.0",
        "wrappy": "1"
      }
    },
    "node_modules/inherits": {
      "version": "2.0.4",
      "resolved": "https://registry.npmjs.org/inherits/-/inherits-2.0.4.tgz",
      "integrity": "sha512-k/vGaX4/Yla3WzyMCvTQOXYeIHvqOKtnqBduzTHpzpQZzAskKMhZ2K+EnBiSM9zGSoIFeMpXKxa4dYeZIQqewQ=="
    },
    "node_modules/intersection-observer": {
      "version": "0.12.2",
      "resolved": "https://registry.npmjs.org/intersection-observer/-/intersection-observer-0.12.2.tgz",
      "integrity": "sha512-7m1vEcPCxXYI8HqnL8CKI6siDyD+eIWSwgB3DZA+ZTogxk9I4CDnj4wilt9x/+/QbHI4YG5YZNmC6458/e9Ktg=="
    },
    "node_modules/invert-kv": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/invert-kv/-/invert-kv-2.0.0.tgz",
      "integrity": "sha512-wPVv/y/QQ/Uiirj/vh3oP+1Ww+AWehmi1g5fFWGPF6IpCBCDVrhgHRMvrLfdYcwDh3QJbGXDW4JAuzxElLSqKA==",
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/iron-webcrypto": {
      "version": "1.2.1",
      "resolved": "https://registry.npmjs.org/iron-webcrypto/-/iron-webcrypto-1.2.1.tgz",
      "integrity": "sha512-feOM6FaSr6rEABp/eDfVseKyTMDt+KGpeB35SkVn9Tyn0CqvVsY3EwI0v5i8nMHyJnzCIQf7nsy3p41TPkJZhg==",
      "funding": {
        "url": "https://github.com/sponsors/brc-dd"
      }
    },
    "node_modules/is-binary-path": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/is-binary-path/-/is-binary-path-2.1.0.tgz",
      "integrity": "sha512-ZMERYes6pDydyuGidse7OsHxtbI7WVeUEozgR/g7rd0xUimYNlvZRE/K2MgZTjWy725IfelLeVcEM97mmtRGXw==",
      "dependencies": {
        "binary-extensions": "^2.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/is-core-module": {
      "version": "2.15.1",
      "resolved": "https://registry.npmjs.org/is-core-module/-/is-core-module-2.15.1.tgz",
      "integrity": "sha512-z0vtXSwucUJtANQWldhbtbt7BnL0vxiFjIdDLAatwhDYty2bad6s+rijD6Ri4YuYJubLzIJLUidCh09e1djEVQ==",
      "dev": true,
      "dependencies": {
        "hasown": "^2.0.2"
      },
      "engines": {
        "node": ">= 0.4"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/is-docker": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/is-docker/-/is-docker-3.0.0.tgz",
      "integrity": "sha512-eljcgEDlEns/7AXFosB5K/2nCM4P7FQPkGc/DWLy5rmFEWvZayGrik1d9/QIY5nJ4f9YsVvBkA6kJpHn9rISdQ==",
      "bin": {
        "is-docker": "cli.js"
      },
      "engines": {
        "node": "^12.20.0 || ^14.13.1 || >=16.0.0"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/is-extglob": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/is-extglob/-/is-extglob-2.1.1.tgz",
      "integrity": "sha512-SbKbANkN603Vi4jEZv49LeVJMn4yGwsbzZworEoyEiutsN3nJYdbO36zfhGJ6QEDpOZIFkDtnq5JRxmvl3jsoQ==",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/is-fullwidth-code-point": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/is-fullwidth-code-point/-/is-fullwidth-code-point-3.0.0.tgz",
      "integrity": "sha512-zymm5+u+sCsSWyD9qNaejV3DFvhCKclKdizYaJUuHA83RLjb7nSuGnddCHGv0hk+KY7BMAlsWeK4Ueg6EV6XQg==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/is-glob": {
      "version": "4.0.3",
      "resolved": "https://registry.npmjs.org/is-glob/-/is-glob-4.0.3.tgz",
      "integrity": "sha512-xelSayHH36ZgE7ZWhli7pW34hNbNl8Ojv5KVmkJD4hBdD3th8Tfk9vYasLM+mXWOZhFkgZfxhLSnrwRr4elSSg==",
      "dependencies": {
        "is-extglob": "^2.1.1"
      },
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/is-hex-prefixed": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/is-hex-prefixed/-/is-hex-prefixed-1.0.0.tgz",
      "integrity": "sha512-WvtOiug1VFrE9v1Cydwm+FnXd3+w9GaeVUss5W4v/SLy3UW00vP+6iNF2SdnfiBoLy4bTqVdkftNGTUeOFVsbA==",
      "engines": {
        "node": ">=6.5.0",
        "npm": ">=3"
      }
    },
    "node_modules/is-inside-container": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/is-inside-container/-/is-inside-container-1.0.0.tgz",
      "integrity": "sha512-KIYLCCJghfHZxqjYBE7rEy0OBuTd5xCHS7tHVgvCLkx7StIoaxwNW3hCALgEUjFfeRk+MG/Qxmp/vtETEF3tRA==",
      "dependencies": {
        "is-docker": "^3.0.0"
      },
      "bin": {
        "is-inside-container": "cli.js"
      },
      "engines": {
        "node": ">=14.16"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/is-number": {
      "version": "7.0.0",
      "resolved": "https://registry.npmjs.org/is-number/-/is-number-7.0.0.tgz",
      "integrity": "sha512-41Cifkg6e8TylSpdtTpeLVMqvSBEVzTttHvERD741+pnZ8ANv0004MRL43QKPDlK9cGvNp6NZWZUBlbGXYxxng==",
      "engines": {
        "node": ">=0.12.0"
      }
    },
    "node_modules/is-path-inside": {
      "version": "3.0.3",
      "resolved": "https://registry.npmjs.org/is-path-inside/-/is-path-inside-3.0.3.tgz",
      "integrity": "sha512-Fd4gABb+ycGAmKou8eMftCupSir5lRxqf4aD/vd0cD2qc4HL07OjCeuHMr8Ro4CoMaeCKDB0/ECBOVWjTwUvPQ==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/is-stream": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/is-stream/-/is-stream-3.0.0.tgz",
      "integrity": "sha512-LnQR4bZ9IADDRSkvpqMGvt/tEJWclzklNgSw48V5EAaAeDd6qGvN8ei6k5p0tvxSR171VmGyHuTiAOfxAbr8kA==",
      "engines": {
        "node": "^12.20.0 || ^14.13.1 || >=16.0.0"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/is-wsl": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/is-wsl/-/is-wsl-3.1.0.tgz",
      "integrity": "sha512-UcVfVfaK4Sc4m7X3dUSoHoozQGBEFeDC+zVo06t98xe8CzHSZZBekNXH+tu0NalHolcJ/QAGqS46Hef7QXBIMw==",
      "dependencies": {
        "is-inside-container": "^1.0.0"
      },
      "engines": {
        "node": ">=16"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/is64bit": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/is64bit/-/is64bit-2.0.0.tgz",
      "integrity": "sha512-jv+8jaWCl0g2lSBkNSVXdzfBA0npK1HGC2KtWM9FumFRoGS94g3NbCCLVnCYHLjp4GrW2KZeeSTMo5ddtznmGw==",
      "dependencies": {
        "system-architecture": "^0.1.0"
      },
      "engines": {
        "node": ">=18"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/isexe": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/isexe/-/isexe-2.0.0.tgz",
      "integrity": "sha512-RHxMLp9lnKHGHRng9QFhRCMbYAcVpn69smSGcq3f36xjgVVWThj4qqLbTLlq7Ssj8B+fIQ1EuCEGI2lKsyQeIw=="
    },
    "node_modules/isomorphic-ws": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/isomorphic-ws/-/isomorphic-ws-4.0.1.tgz",
      "integrity": "sha512-BhBvN2MBpWTaSHdWRb/bwdZJ1WaehQ2L1KngkCkfLUGF0mAWAT1sQUQacEmQ0jXkFw/czDXPNQSL5u2/Krsz1w==",
      "peerDependencies": {
        "ws": "*"
      }
    },
    "node_modules/isows": {
      "version": "1.0.6",
      "resolved": "https://registry.npmjs.org/isows/-/isows-1.0.6.tgz",
      "integrity": "sha512-lPHCayd40oW98/I0uvgaHKWCSvkzY27LjWLbtzOm64yQ+G3Q5npjjbdppU65iZXkK1Zt+kH9pfegli0AYfwYYw==",
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/wevm"
        }
      ],
      "peerDependencies": {
        "ws": "*"
      }
    },
    "node_modules/jackspeak": {
      "version": "3.4.3",
      "resolved": "https://registry.npmjs.org/jackspeak/-/jackspeak-3.4.3.tgz",
      "integrity": "sha512-OGlZQpz2yfahA/Rd1Y8Cd9SIEsqvXkLVoSw/cgwhnhFMDbsQFeZYoJJ7bIZBS9BcamUW96asq/npPWugM+RQBw==",
      "dev": true,
      "dependencies": {
        "@isaacs/cliui": "^8.0.2"
      },
      "funding": {
        "url": "https://github.com/sponsors/isaacs"
      },
      "optionalDependencies": {
        "@pkgjs/parseargs": "^0.11.0"
      }
    },
    "node_modules/jayson": {
      "version": "4.1.2",
      "resolved": "https://registry.npmjs.org/jayson/-/jayson-4.1.2.tgz",
      "integrity": "sha512-5nzMWDHy6f+koZOuYsArh2AXs73NfWYVlFyJJuCedr93GpY+Ku8qq10ropSXVfHK+H0T6paA88ww+/dV+1fBNA==",
      "dependencies": {
        "@types/connect": "^3.4.33",
        "@types/node": "^12.12.54",
        "@types/ws": "^7.4.4",
        "commander": "^2.20.3",
        "delay": "^5.0.0",
        "es6-promisify": "^5.0.0",
        "eyes": "^0.1.8",
        "isomorphic-ws": "^4.0.1",
        "json-stringify-safe": "^5.0.1",
        "JSONStream": "^1.3.5",
        "uuid": "^8.3.2",
        "ws": "^7.5.10"
      },
      "bin": {
        "jayson": "bin/jayson.js"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/jayson/node_modules/@types/node": {
      "version": "12.20.55",
      "resolved": "https://registry.npmjs.org/@types/node/-/node-12.20.55.tgz",
      "integrity": "sha512-J8xLz7q2OFulZ2cyGTLE1TbbZcjpno7FaN6zdJNrgAdrJ+DZzh/uFR6YrTb4C+nXakvud8Q4+rbhoIWlYQbUFQ=="
    },
    "node_modules/jayson/node_modules/@types/ws": {
      "version": "7.4.7",
      "resolved": "https://registry.npmjs.org/@types/ws/-/ws-7.4.7.tgz",
      "integrity": "sha512-JQbbmxZTZehdc2iszGKs5oC3NFnjeay7mtAWrdt7qNtAVK0g19muApzAy4bm9byz79xa2ZnO/BOBC2R8RC5Lww==",
      "dependencies": {
        "@types/node": "*"
      }
    },
    "node_modules/jayson/node_modules/ws": {
      "version": "7.5.10",
      "resolved": "https://registry.npmjs.org/ws/-/ws-7.5.10.tgz",
      "integrity": "sha512-+dbF1tHwZpXcbOJdVOkzLDxZP1ailvSxM6ZweXTegylPny803bFhA+vqBYw4s31NSAk4S2Qz+AKXK9a4wkdjcQ==",
      "engines": {
        "node": ">=8.3.0"
      },
      "peerDependencies": {
        "bufferutil": "^4.0.1",
        "utf-8-validate": "^5.0.2"
      },
      "peerDependenciesMeta": {
        "bufferutil": {
          "optional": true
        },
        "utf-8-validate": {
          "optional": true
        }
      }
    },
    "node_modules/jiti": {
      "version": "1.21.6",
      "resolved": "https://registry.npmjs.org/jiti/-/jiti-1.21.6.tgz",
      "integrity": "sha512-2yTgeWTWzMWkHu6Jp9NKgePDaYHbntiwvYuuJLbbN9vl7DC9DvXKOB2BC3ZZ92D3cvV/aflH0osDfwpHepQ53w==",
      "dev": true,
      "bin": {
        "jiti": "bin/jiti.js"
      }
    },
    "node_modules/joi": {
      "version": "17.13.3",
      "resolved": "https://registry.npmjs.org/joi/-/joi-17.13.3.tgz",
      "integrity": "sha512-otDA4ldcIx+ZXsKHWmp0YizCweVRZG96J10b0FevjfuncLO1oX59THoAmHkNubYJ+9gWsYsp5k8v4ib6oDv1fA==",
      "dependencies": {
        "@hapi/hoek": "^9.3.0",
        "@hapi/topo": "^5.1.0",
        "@sideway/address": "^4.1.5",
        "@sideway/formula": "^3.0.1",
        "@sideway/pinpoint": "^2.0.0"
      }
    },
    "node_modules/js-cookie": {
      "version": "3.0.5",
      "resolved": "https://registry.npmjs.org/js-cookie/-/js-cookie-3.0.5.tgz",
      "integrity": "sha512-cEiJEAEoIbWfCZYKWhVwFuvPX1gETRYPw6LlaTKoxD3s2AkXzkCjnp6h0V77ozyqj0jakteJ4YqDJT830+lVGw==",
      "engines": {
        "node": ">=14"
      }
    },
    "node_modules/js-tokens": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/js-tokens/-/js-tokens-4.0.0.tgz",
      "integrity": "sha512-RdJUflcE3cUzKiMqQgsCu06FPu9UdIJO0beYbPhHN4k6apgJtifcoCtT9bcxOpYBtpD2kCM6Sbzg4CausW/PKQ=="
    },
    "node_modules/js-yaml": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/js-yaml/-/js-yaml-4.1.0.tgz",
      "integrity": "sha512-wpxZs9NoxZaJESJGIZTyDEaYpl0FKSA+FB9aJiyemKhMwkxQg63h4T1KJgUGHpTqPDNRcmmYLugrRjJlBtWvRA==",
      "dev": true,
      "dependencies": {
        "argparse": "^2.0.1"
      },
      "bin": {
        "js-yaml": "bin/js-yaml.js"
      }
    },
    "node_modules/jsesc": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/jsesc/-/jsesc-3.0.2.tgz",
      "integrity": "sha512-xKqzzWXDttJuOcawBt4KnKHHIf5oQ/Cxax+0PWFG+DFDgHNAdi+TXECADI+RYiFUMmx8792xsMbbgXj4CwnP4g==",
      "dev": true,
      "bin": {
        "jsesc": "bin/jsesc"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/json-buffer": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/json-buffer/-/json-buffer-3.0.1.tgz",
      "integrity": "sha512-4bV5BfR2mqfQTJm+V5tPPdf+ZpuhiIvTuAB5g8kcrXOZpTT/QwwVRWBywX1ozr6lEuPdbHxwaJlm9G6mI2sfSQ==",
      "dev": true
    },
    "node_modules/json-rpc-engine": {
      "version": "6.1.0",
      "resolved": "https://registry.npmjs.org/json-rpc-engine/-/json-rpc-engine-6.1.0.tgz",
      "integrity": "sha512-NEdLrtrq1jUZyfjkr9OCz9EzCNhnRyWtt1PAnvnhwy6e8XETS0Dtc+ZNCO2gvuAoKsIn2+vCSowXTYE4CkgnAQ==",
      "dependencies": {
        "@metamask/safe-event-emitter": "^2.0.0",
        "eth-rpc-errors": "^4.0.2"
      },
      "engines": {
        "node": ">=10.0.0"
      }
    },
    "node_modules/json-rpc-engine/node_modules/@metamask/safe-event-emitter": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/@metamask/safe-event-emitter/-/safe-event-emitter-2.0.0.tgz",
      "integrity": "sha512-/kSXhY692qiV1MXu6EeOZvg5nECLclxNXcKCxJ3cXQgYuRymRHpdx/t7JXfsK+JLjwA1e1c1/SBrlQYpusC29Q=="
    },
    "node_modules/json-rpc-random-id": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/json-rpc-random-id/-/json-rpc-random-id-1.0.1.tgz",
      "integrity": "sha512-RJ9YYNCkhVDBuP4zN5BBtYAzEl03yq/jIIsyif0JY9qyJuQQZNeDK7anAPKKlyEtLSj2s8h6hNh2F8zO5q7ScA=="
    },
    "node_modules/json-schema-traverse": {
      "version": "0.4.1",
      "resolved": "https://registry.npmjs.org/json-schema-traverse/-/json-schema-traverse-0.4.1.tgz",
      "integrity": "sha512-xbbCH5dCYU5T8LcEhhuh7HJ88HXuW3qsI3Y0zOZFKfZEHcpWiHU/Jxzk629Brsab/mMiHQti9wMP+845RPe3Vg==",
      "dev": true
    },
    "node_modules/json-stable-stringify-without-jsonify": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/json-stable-stringify-without-jsonify/-/json-stable-stringify-without-jsonify-1.0.1.tgz",
      "integrity": "sha512-Bdboy+l7tA3OGW6FjyFHWkP5LuByj1Tk33Ljyq0axyzdk9//JSi2u3fP1QSmd1KNwq6VOKYGlAu87CisVir6Pw==",
      "dev": true
    },
    "node_modules/json-stringify-safe": {
      "version": "5.0.1",
      "resolved": "https://registry.npmjs.org/json-stringify-safe/-/json-stringify-safe-5.0.1.tgz",
      "integrity": "sha512-ZClg6AaYvamvYEE82d3Iyd3vSSIjQ+odgjaTzRuO3s7toCdFKczob2i0zCh7JE8kWn17yvAWhUVxvqGwUalsRA=="
    },
    "node_modules/json-toy": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/json-toy/-/json-toy-2.0.2.tgz",
      "integrity": "sha512-TUmg03hrH2xKLJ+72Dpwo4yKmxZYcPT0HNu5gyq1uV5lD7B/X6RXhU2BhMZssfzFxF4kUkEXjrZ5aWWqKmaF2A==",
      "dependencies": {
        "clipboardy": "^1.2.3",
        "yargs": "^12.0.1"
      },
      "bin": {
        "j-tree-str": "bin/j-tree-str.js",
        "jtls": "bin/jtls.js",
        "jts": "bin/j-tree-str.js"
      },
      "engines": {
        "node": ">= 6.0",
        "npm": ">= 3"
      }
    },
    "node_modules/json-toy/node_modules/ansi-regex": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/ansi-regex/-/ansi-regex-3.0.1.tgz",
      "integrity": "sha512-+O9Jct8wf++lXxxFc4hc8LsjaSq0HFzzL7cVsw8pRDIPdjKD2mT4ytDZlLuSBZ4cLKZFXIrMGO7DbQCtMJJMKw==",
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/json-toy/node_modules/clipboardy": {
      "version": "1.2.3",
      "resolved": "https://registry.npmjs.org/clipboardy/-/clipboardy-1.2.3.tgz",
      "integrity": "sha512-2WNImOvCRe6r63Gk9pShfkwXsVtKCroMAevIbiae021mS850UkWPbevxsBz3tnvjZIEGvlwaqCPsw+4ulzNgJA==",
      "dependencies": {
        "arch": "^2.1.0",
        "execa": "^0.8.0"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/json-toy/node_modules/cliui": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/cliui/-/cliui-4.1.0.tgz",
      "integrity": "sha512-4FG+RSG9DL7uEwRUZXZn3SS34DiDPfzP0VOiEwtUWlE+AR2EIg+hSyvrIgUUfhdgR/UkAeW2QHgeP+hWrXs7jQ==",
      "dependencies": {
        "string-width": "^2.1.1",
        "strip-ansi": "^4.0.0",
        "wrap-ansi": "^2.0.0"
      }
    },
    "node_modules/json-toy/node_modules/cross-spawn": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/cross-spawn/-/cross-spawn-5.1.0.tgz",
      "integrity": "sha512-pTgQJ5KC0d2hcY8eyL1IzlBPYjTkyH72XRZPnLyKus2mBfNjQs3klqbJU2VILqZryAZUt9JOb3h/mWMy23/f5A==",
      "dependencies": {
        "lru-cache": "^4.0.1",
        "shebang-command": "^1.2.0",
        "which": "^1.2.9"
      }
    },
    "node_modules/json-toy/node_modules/execa": {
      "version": "0.8.0",
      "resolved": "https://registry.npmjs.org/execa/-/execa-0.8.0.tgz",
      "integrity": "sha512-zDWS+Rb1E8BlqqhALSt9kUhss8Qq4nN3iof3gsOdyINksElaPyNBtKUMTR62qhvgVWR0CqCX7sdnKe4MnUbFEA==",
      "dependencies": {
        "cross-spawn": "^5.0.1",
        "get-stream": "^3.0.0",
        "is-stream": "^1.1.0",
        "npm-run-path": "^2.0.0",
        "p-finally": "^1.0.0",
        "signal-exit": "^3.0.0",
        "strip-eof": "^1.0.0"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/json-toy/node_modules/find-up": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/find-up/-/find-up-3.0.0.tgz",
      "integrity": "sha512-1yD6RmLI1XBfxugvORwlck6f75tYL+iR0jqwsOrOxMZyGYqUuDhJ0l4AXdO1iX/FTs9cBAMEk1gWSEx1kSbylg==",
      "dependencies": {
        "locate-path": "^3.0.0"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/json-toy/node_modules/get-caller-file": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/get-caller-file/-/get-caller-file-1.0.3.tgz",
      "integrity": "sha512-3t6rVToeoZfYSGd8YoLFR2DJkiQrIiUrGcjvFX2mDw3bn6k2OtwHN0TNCLbBO+w8qTvimhDkv+LSscbJY1vE6w=="
    },
    "node_modules/json-toy/node_modules/get-stream": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/get-stream/-/get-stream-3.0.0.tgz",
      "integrity": "sha512-GlhdIUuVakc8SJ6kK0zAFbiGzRFzNnY4jUuEbV9UROo4Y+0Ny4fjvcZFVTeDA4odpFyOQzaw6hXukJSq/f28sQ==",
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/json-toy/node_modules/is-fullwidth-code-point": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/is-fullwidth-code-point/-/is-fullwidth-code-point-2.0.0.tgz",
      "integrity": "sha512-VHskAKYM8RfSFXwee5t5cbN5PZeq1Wrh6qd5bkyiXIf6UQcN6w/A0eXM9r6t8d+GYOh+o6ZhiEnb88LN/Y8m2w==",
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/json-toy/node_modules/is-stream": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/is-stream/-/is-stream-1.1.0.tgz",
      "integrity": "sha512-uQPm8kcs47jx38atAcWTVxyltQYoPT68y9aWYdV6yWXSyW8mzSat0TL6CiWdZeCdF3KrAvpVtnHbTv4RN+rqdQ==",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/json-toy/node_modules/locate-path": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/locate-path/-/locate-path-3.0.0.tgz",
      "integrity": "sha512-7AO748wWnIhNqAuaty2ZWHkQHRSNfPVIsPIfwEOWO22AmaoVrWavlOcMR5nzTLNYvp36X220/maaRsrec1G65A==",
      "dependencies": {
        "p-locate": "^3.0.0",
        "path-exists": "^3.0.0"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/json-toy/node_modules/lru-cache": {
      "version": "4.1.5",
      "resolved": "https://registry.npmjs.org/lru-cache/-/lru-cache-4.1.5.tgz",
      "integrity": "sha512-sWZlbEP2OsHNkXrMl5GYk/jKk70MBng6UU4YI/qGDYbgf6YbP4EvmqISbXCoJiRKs+1bSpFHVgQxvJ17F2li5g==",
      "dependencies": {
        "pseudomap": "^1.0.2",
        "yallist": "^2.1.2"
      }
    },
    "node_modules/json-toy/node_modules/npm-run-path": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/npm-run-path/-/npm-run-path-2.0.2.tgz",
      "integrity": "sha512-lJxZYlT4DW/bRUtFh1MQIWqmLwQfAxnqWG4HhEdjMlkrJYnJn0Jrr2u3mgxqaWsdiBc76TYkTG/mhrnYTuzfHw==",
      "dependencies": {
        "path-key": "^2.0.0"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/json-toy/node_modules/p-limit": {
      "version": "2.3.0",
      "resolved": "https://registry.npmjs.org/p-limit/-/p-limit-2.3.0.tgz",
      "integrity": "sha512-//88mFWSJx8lxCzwdAABTJL2MyWB12+eIY7MDL2SqLmAkeKU9qxRvWuSyTjm3FUmpBEMuFfckAIqEaVGUDxb6w==",
      "dependencies": {
        "p-try": "^2.0.0"
      },
      "engines": {
        "node": ">=6"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/json-toy/node_modules/p-locate": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/p-locate/-/p-locate-3.0.0.tgz",
      "integrity": "sha512-x+12w/To+4GFfgJhBEpiDcLozRJGegY+Ei7/z0tSLkMmxGZNybVMSfWj9aJn8Z5Fc7dBUNJOOVgPv2H7IwulSQ==",
      "dependencies": {
        "p-limit": "^2.0.0"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/json-toy/node_modules/path-exists": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/path-exists/-/path-exists-3.0.0.tgz",
      "integrity": "sha512-bpC7GYwiDYQ4wYLe+FA8lhRjhQCMcQGuSgGGqDkg/QerRWw9CmGRT0iSOVRSZJ29NMLZgIzqaljJ63oaL4NIJQ==",
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/json-toy/node_modules/path-key": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/path-key/-/path-key-2.0.1.tgz",
      "integrity": "sha512-fEHGKCSmUSDPv4uoj8AlD+joPlq3peND+HRYyxFz4KPw4z926S/b8rIuFs2FYJg3BwsxJf6A9/3eIdLaYC+9Dw==",
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/json-toy/node_modules/require-main-filename": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/require-main-filename/-/require-main-filename-1.0.1.tgz",
      "integrity": "sha512-IqSUtOVP4ksd1C/ej5zeEh/BIP2ajqpn8c5x+q99gvcIG/Qf0cud5raVnE/Dwd0ua9TXYDoDc0RE5hBSdz22Ug=="
    },
    "node_modules/json-toy/node_modules/shebang-command": {
      "version": "1.2.0",
      "resolved": "https://registry.npmjs.org/shebang-command/-/shebang-command-1.2.0.tgz",
      "integrity": "sha512-EV3L1+UQWGor21OmnvojK36mhg+TyIKDh3iFBKBohr5xeXIhNBcx8oWdgkTEEQ+BEFFYdLRuqMfd5L84N1V5Vg==",
      "dependencies": {
        "shebang-regex": "^1.0.0"
      },
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/json-toy/node_modules/shebang-regex": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/shebang-regex/-/shebang-regex-1.0.0.tgz",
      "integrity": "sha512-wpoSFAxys6b2a2wHZ1XpDSgD7N9iVjg29Ph9uV/uaP9Ex/KXlkTZTeddxDPSYQpgvzKLGJke2UU0AzoGCjNIvQ==",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/json-toy/node_modules/signal-exit": {
      "version": "3.0.7",
      "resolved": "https://registry.npmjs.org/signal-exit/-/signal-exit-3.0.7.tgz",
      "integrity": "sha512-wnD2ZE+l+SPC/uoS0vXeE9L1+0wuaMqKlfz9AMUo38JsyLSBWSFcHR1Rri62LZc12vLr1gb3jl7iwQhgwpAbGQ=="
    },
    "node_modules/json-toy/node_modules/string-width": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/string-width/-/string-width-2.1.1.tgz",
      "integrity": "sha512-nOqH59deCq9SRHlxq1Aw85Jnt4w6KvLKqWVik6oA9ZklXLNIOlqg4F2yrT1MVaTjAqvVwdfeZ7w7aCvJD7ugkw==",
      "dependencies": {
        "is-fullwidth-code-point": "^2.0.0",
        "strip-ansi": "^4.0.0"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/json-toy/node_modules/strip-ansi": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/strip-ansi/-/strip-ansi-4.0.0.tgz",
      "integrity": "sha512-4XaJ2zQdCzROZDivEVIDPkcQn8LMFSa8kj8Gxb/Lnwzv9A8VctNZ+lfivC/sV3ivW8ElJTERXZoPBRrZKkNKow==",
      "dependencies": {
        "ansi-regex": "^3.0.0"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/json-toy/node_modules/which": {
      "version": "1.3.1",
      "resolved": "https://registry.npmjs.org/which/-/which-1.3.1.tgz",
      "integrity": "sha512-HxJdYWq1MTIQbJ3nw0cqssHoTNU267KlrDuGZ1WYlxDStUtKUhOaJmh112/TZmHxxUfuJqPXSOm7tDyas0OSIQ==",
      "dependencies": {
        "isexe": "^2.0.0"
      },
      "bin": {
        "which": "bin/which"
      }
    },
    "node_modules/json-toy/node_modules/wrap-ansi": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/wrap-ansi/-/wrap-ansi-2.1.0.tgz",
      "integrity": "sha512-vAaEaDM946gbNpH5pLVNR+vX2ht6n0Bt3GXwVB1AuAqZosOvHNF3P7wDnh8KLkSqgUh0uh77le7Owgoz+Z9XBw==",
      "dependencies": {
        "string-width": "^1.0.1",
        "strip-ansi": "^3.0.1"
      },
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/json-toy/node_modules/wrap-ansi/node_modules/ansi-regex": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/ansi-regex/-/ansi-regex-2.1.1.tgz",
      "integrity": "sha512-TIGnTpdo+E3+pCyAluZvtED5p5wCqLdezCyhPZzKPcxvFplEt4i+W7OONCKgeZFT3+y5NZZfOOS/Bdcanm1MYA==",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/json-toy/node_modules/wrap-ansi/node_modules/is-fullwidth-code-point": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/is-fullwidth-code-point/-/is-fullwidth-code-point-1.0.0.tgz",
      "integrity": "sha512-1pqUqRjkhPJ9miNq9SwMfdvi6lBJcd6eFxvfaivQhaH3SgisfiuudvFntdKOmxuee/77l+FPjKrQjWvmPjWrRw==",
      "dependencies": {
        "number-is-nan": "^1.0.0"
      },
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/json-toy/node_modules/wrap-ansi/node_modules/string-width": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/string-width/-/string-width-1.0.2.tgz",
      "integrity": "sha512-0XsVpQLnVCXHJfyEs8tC0zpTVIr5PKKsQtkT29IwupnPTjtPmQ3xT/4yCREF9hYkV/3M3kzcUTSAZT6a6h81tw==",
      "dependencies": {
        "code-point-at": "^1.0.0",
        "is-fullwidth-code-point": "^1.0.0",
        "strip-ansi": "^3.0.0"
      },
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/json-toy/node_modules/wrap-ansi/node_modules/strip-ansi": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/strip-ansi/-/strip-ansi-3.0.1.tgz",
      "integrity": "sha512-VhumSSbBqDTP8p2ZLKj40UjBCV4+v8bUSEpUb4KjRgWk9pbqGF4REFj6KEagidb2f/M6AzC0EmFyDNGaw9OCzg==",
      "dependencies": {
        "ansi-regex": "^2.0.0"
      },
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/json-toy/node_modules/yallist": {
      "version": "2.1.2",
      "resolved": "https://registry.npmjs.org/yallist/-/yallist-2.1.2.tgz",
      "integrity": "sha512-ncTzHV7NvsQZkYe1DW7cbDLm0YpzHmZF5r/iyP3ZnQtMiJ+pjzisCiMNI+Sj+xQF5pXhSHxSB3uDbsBTzY/c2A=="
    },
    "node_modules/json-toy/node_modules/yargs": {
      "version": "12.0.5",
      "resolved": "https://registry.npmjs.org/yargs/-/yargs-12.0.5.tgz",
      "integrity": "sha512-Lhz8TLaYnxq/2ObqHDql8dX8CJi97oHxrjUcYtzKbbykPtVW9WB+poxI+NM2UIzsMgNCZTIf0AQwsjK5yMAqZw==",
      "dependencies": {
        "cliui": "^4.0.0",
        "decamelize": "^1.2.0",
        "find-up": "^3.0.0",
        "get-caller-file": "^1.0.1",
        "os-locale": "^3.0.0",
        "require-directory": "^2.1.1",
        "require-main-filename": "^1.0.1",
        "set-blocking": "^2.0.0",
        "string-width": "^2.0.0",
        "which-module": "^2.0.0",
        "y18n": "^3.2.1 || ^4.0.0",
        "yargs-parser": "^11.1.1"
      }
    },
    "node_modules/json-toy/node_modules/yargs-parser": {
      "version": "11.1.1",
      "resolved": "https://registry.npmjs.org/yargs-parser/-/yargs-parser-11.1.1.tgz",
      "integrity": "sha512-C6kB/WJDiaxONLJQnF8ccx9SEeoTTLek8RVbaOIsrAUS8VrBEXfmeSnCZxygc+XC2sNMBIwOOnfcxiynjHsVSQ==",
      "dependencies": {
        "camelcase": "^5.0.0",
        "decamelize": "^1.2.0"
      }
    },
    "node_modules/json2mq": {
      "version": "0.2.0",
      "resolved": "https://registry.npmjs.org/json2mq/-/json2mq-0.2.0.tgz",
      "integrity": "sha512-SzoRg7ux5DWTII9J2qkrZrqV1gt+rTaoufMxEzXbS26Uid0NwaJd123HcoB80TgubEppxxIGdNxCx50fEoEWQA==",
      "dependencies": {
        "string-convert": "^0.2.0"
      }
    },
    "node_modules/json5": {
      "version": "2.2.3",
      "resolved": "https://registry.npmjs.org/json5/-/json5-2.2.3.tgz",
      "integrity": "sha512-XmOWe7eyHYH14cLdVPoyg+GOH3rYX++KpzrylJwSW98t3Nk+U8XOl8FWKOgwtzdb8lXGf6zYwDUzeHMWfxasyg==",
      "dev": true,
      "bin": {
        "json5": "lib/cli.js"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/jsonparse": {
      "version": "1.3.1",
      "resolved": "https://registry.npmjs.org/jsonparse/-/jsonparse-1.3.1.tgz",
      "integrity": "sha512-POQXvpdL69+CluYsillJ7SUhKvytYjW9vG/GKpnf+xP8UWgYEM/RaMzHHofbALDiKbbP1W8UEYmgGl39WkPZsg==",
      "engines": [
        "node >= 0.2.0"
      ]
    },
    "node_modules/JSONStream": {
      "version": "1.3.5",
      "resolved": "https://registry.npmjs.org/JSONStream/-/JSONStream-1.3.5.tgz",
      "integrity": "sha512-E+iruNOY8VV9s4JEbe1aNEm6MiszPRr/UfcHMz0TQh1BXSxHK+ASV1R6W4HpjBhSeS+54PIsAMCBmwD06LLsqQ==",
      "dependencies": {
        "jsonparse": "^1.2.0",
        "through": ">=2.2.7 <3"
      },
      "bin": {
        "JSONStream": "bin.js"
      },
      "engines": {
        "node": "*"
      }
    },
    "node_modules/keccak": {
      "version": "3.0.4",
      "resolved": "https://registry.npmjs.org/keccak/-/keccak-3.0.4.tgz",
      "integrity": "sha512-3vKuW0jV8J3XNTzvfyicFR5qvxrSAGl7KIhvgOu5cmWwM7tZRj3fMbj/pfIf4be7aznbc+prBWGjywox/g2Y6Q==",
      "hasInstallScript": true,
      "dependencies": {
        "node-addon-api": "^2.0.0",
        "node-gyp-build": "^4.2.0",
        "readable-stream": "^3.6.0"
      },
      "engines": {
        "node": ">=10.0.0"
      }
    },
    "node_modules/keyv": {
      "version": "4.5.4",
      "resolved": "https://registry.npmjs.org/keyv/-/keyv-4.5.4.tgz",
      "integrity": "sha512-oxVHkHR/EJf2CNXnWxRLW6mg7JyCCUcG0DtEGmL2ctUo1PNTin1PUil+r/+4r5MpVgC/fn1kjsx7mjSujKqIpw==",
      "dev": true,
      "dependencies": {
        "json-buffer": "3.0.1"
      }
    },
    "node_modules/keyvaluestorage-interface": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/keyvaluestorage-interface/-/keyvaluestorage-interface-1.0.0.tgz",
      "integrity": "sha512-8t6Q3TclQ4uZynJY9IGr2+SsIGwK9JHcO6ootkHCGA0CrQCRy+VkouYNO2xicET6b9al7QKzpebNow+gkpCL8g=="
    },
    "node_modules/lazy-ass": {
      "version": "1.6.0",
      "resolved": "https://registry.npmjs.org/lazy-ass/-/lazy-ass-1.6.0.tgz",
      "integrity": "sha512-cc8oEVoctTvsFZ/Oje/kGnHbpWHYBe8IAJe4C0QNc3t8uM/0Y8+erSz/7Y1ALuXTEZTMvxXwO6YbX1ey3ujiZw==",
      "engines": {
        "node": "> 0.8"
      }
    },
    "node_modules/lcid": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/lcid/-/lcid-2.0.0.tgz",
      "integrity": "sha512-avPEb8P8EGnwXKClwsNUgryVjllcRqtMYa49NTsbQagYuT1DcXnl1915oxWjoyGrXR6zH/Y0Zc96xWsPcoDKeA==",
      "dependencies": {
        "invert-kv": "^2.0.0"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/levn": {
      "version": "0.4.1",
      "resolved": "https://registry.npmjs.org/levn/-/levn-0.4.1.tgz",
      "integrity": "sha512-+bT2uH4E5LGE7h/n3evcS/sQlJXCpIp6ym8OWJ5eV6+67Dsql/LaaT7qJBAt2rzfoa/5QBGBhxDix1dMt2kQKQ==",
      "dev": true,
      "dependencies": {
        "prelude-ls": "^1.2.1",
        "type-check": "~0.4.0"
      },
      "engines": {
        "node": ">= 0.8.0"
      }
    },
    "node_modules/libphonenumber-js": {
      "version": "1.11.12",
      "resolved": "https://registry.npmjs.org/libphonenumber-js/-/libphonenumber-js-1.11.12.tgz",
      "integrity": "sha512-QkJn9/D7zZ1ucvT++TQSvZuSA2xAWeUytU+DiEQwbPKLyrDpvbul2AFs1CGbRAPpSCCk47aRAb5DX5mmcayp4g=="
    },
    "node_modules/lilconfig": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/lilconfig/-/lilconfig-2.1.0.tgz",
      "integrity": "sha512-utWOt/GHzuUxnLKxB6dk81RoOeoNeHgbrXiuGk4yyF5qlRz+iIVWu56E2fqGHFrXz0QNUhLB/8nKqvRH66JKGQ==",
      "dev": true,
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/lines-and-columns": {
      "version": "1.2.4",
      "resolved": "https://registry.npmjs.org/lines-and-columns/-/lines-and-columns-1.2.4.tgz",
      "integrity": "sha512-7ylylesZQ/PV29jhEDl3Ufjo6ZX7gCqJr5F7PKrqc93v7fzSymt1BpwEU8nAUXs8qzzvqhbjhK5QZg6Mt/HkBg==",
      "dev": true
    },
    "node_modules/listhen": {
      "version": "1.9.0",
      "resolved": "https://registry.npmjs.org/listhen/-/listhen-1.9.0.tgz",
      "integrity": "sha512-I8oW2+QL5KJo8zXNWX046M134WchxsXC7SawLPvRQpogCbkyQIaFxPE89A2HiwR7vAK2Dm2ERBAmyjTYGYEpBg==",
      "dependencies": {
        "@parcel/watcher": "^2.4.1",
        "@parcel/watcher-wasm": "^2.4.1",
        "citty": "^0.1.6",
        "clipboardy": "^4.0.0",
        "consola": "^3.2.3",
        "crossws": ">=0.2.0 <0.4.0",
        "defu": "^6.1.4",
        "get-port-please": "^3.1.2",
        "h3": "^1.12.0",
        "http-shutdown": "^1.2.2",
        "jiti": "^2.1.2",
        "mlly": "^1.7.1",
        "node-forge": "^1.3.1",
        "pathe": "^1.1.2",
        "std-env": "^3.7.0",
        "ufo": "^1.5.4",
        "untun": "^0.1.3",
        "uqr": "^0.1.2"
      },
      "bin": {
        "listen": "bin/listhen.mjs",
        "listhen": "bin/listhen.mjs"
      }
    },
    "node_modules/listhen/node_modules/jiti": {
      "version": "2.4.0",
      "resolved": "https://registry.npmjs.org/jiti/-/jiti-2.4.0.tgz",
      "integrity": "sha512-H5UpaUI+aHOqZXlYOaFP/8AzKsg+guWu+Pr3Y8i7+Y3zr1aXAvCvTAQ1RxSc6oVD8R8c7brgNtTVP91E7upH/g==",
      "bin": {
        "jiti": "lib/jiti-cli.mjs"
      }
    },
    "node_modules/lit": {
      "version": "2.8.0",
      "resolved": "https://registry.npmjs.org/lit/-/lit-2.8.0.tgz",
      "integrity": "sha512-4Sc3OFX9QHOJaHbmTMk28SYgVxLN3ePDjg7hofEft2zWlehFL3LiAuapWc4U/kYwMYJSh2hTCPZ6/LIC7ii0MA==",
      "dependencies": {
        "@lit/reactive-element": "^1.6.0",
        "lit-element": "^3.3.0",
        "lit-html": "^2.8.0"
      }
    },
    "node_modules/lit-element": {
      "version": "3.3.3",
      "resolved": "https://registry.npmjs.org/lit-element/-/lit-element-3.3.3.tgz",
      "integrity": "sha512-XbeRxmTHubXENkV4h8RIPyr8lXc+Ff28rkcQzw3G6up2xg5E8Zu1IgOWIwBLEQsu3cOVFqdYwiVi0hv0SlpqUA==",
      "dependencies": {
        "@lit-labs/ssr-dom-shim": "^1.1.0",
        "@lit/reactive-element": "^1.3.0",
        "lit-html": "^2.8.0"
      }
    },
    "node_modules/lit-html": {
      "version": "2.8.0",
      "resolved": "https://registry.npmjs.org/lit-html/-/lit-html-2.8.0.tgz",
      "integrity": "sha512-o9t+MQM3P4y7M7yNzqAyjp7z+mQGa4NS4CxiyLqFPyFWyc4O+nodLrkrxSaCTrla6M5YOLaT3RpbbqjszB5g3Q==",
      "dependencies": {
        "@types/trusted-types": "^2.0.2"
      }
    },
    "node_modules/locate-path": {
      "version": "6.0.0",
      "resolved": "https://registry.npmjs.org/locate-path/-/locate-path-6.0.0.tgz",
      "integrity": "sha512-iPZK6eYjbxRu3uB4/WZ3EsEIMJFMqAoopl3R+zuq0UjcAm/MO6KCweDgPfP3elTztoKP3KtnVHxTn2NHBSDVUw==",
      "dev": true,
      "dependencies": {
        "p-locate": "^5.0.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/lodash": {
      "version": "4.17.21",
      "resolved": "https://registry.npmjs.org/lodash/-/lodash-4.17.21.tgz",
      "integrity": "sha512-v2kDEe57lecTulaDIuNTPy3Ry4gLGJ6Z1O3vE1krgXZNrsQ+LFTGHVxVjcXPs17LhbZVGedAJv8XZ1tvj5FvSg=="
    },
    "node_modules/lodash.isequal": {
      "version": "4.5.0",
      "resolved": "https://registry.npmjs.org/lodash.isequal/-/lodash.isequal-4.5.0.tgz",
      "integrity": "sha512-pDo3lu8Jhfjqls6GkMgpahsF9kCyayhgykjyLMNFTKWrpVdAQtYyB4muAMWozBB4ig/dtWAmsMxLEI8wuz+DYQ=="
    },
    "node_modules/lodash.merge": {
      "version": "4.6.2",
      "resolved": "https://registry.npmjs.org/lodash.merge/-/lodash.merge-4.6.2.tgz",
      "integrity": "sha512-0KpjqXRVvrYyCsX1swR/XTK0va6VQkQM6MNo7PqW77ByjAhoARA8EfrP1N4+KlKj8YS0ZUCtRT/YUuhyYDujIQ==",
      "dev": true
    },
    "node_modules/loose-envify": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/loose-envify/-/loose-envify-1.4.0.tgz",
      "integrity": "sha512-lyuxPGr/Wfhrlem2CL/UcnUc1zcqKAImBDzukY7Y5F/yQiNdko6+fRLevlw1HgMySw7f611UIY408EtxRSoK3Q==",
      "dependencies": {
        "js-tokens": "^3.0.0 || ^4.0.0"
      },
      "bin": {
        "loose-envify": "cli.js"
      }
    },
    "node_modules/lottie-react": {
      "version": "2.4.0",
      "resolved": "https://registry.npmjs.org/lottie-react/-/lottie-react-2.4.0.tgz",
      "integrity": "sha512-pDJGj+AQlnlyHvOHFK7vLdsDcvbuqvwPZdMlJ360wrzGFurXeKPr8SiRCjLf3LrNYKANQtSsh5dz9UYQHuqx4w==",
      "dependencies": {
        "lottie-web": "^5.10.2"
      },
      "peerDependencies": {
        "react": "^16.8.0 || ^17.0.0 || ^18.0.0",
        "react-dom": "^16.8.0 || ^17.0.0 || ^18.0.0"
      }
    },
    "node_modules/lottie-web": {
      "version": "5.12.2",
      "resolved": "https://registry.npmjs.org/lottie-web/-/lottie-web-5.12.2.tgz",
      "integrity": "sha512-uvhvYPC8kGPjXT3MyKMrL3JitEAmDMp30lVkuq/590Mw9ok6pWcFCwXJveo0t5uqYw1UREQHofD+jVpdjBv8wg=="
    },
    "node_modules/lru-cache": {
      "version": "5.1.1",
      "resolved": "https://registry.npmjs.org/lru-cache/-/lru-cache-5.1.1.tgz",
      "integrity": "sha512-KpNARQA3Iwv+jTA0utUVVbrh+Jlrr1Fv0e56GGzAFOXN7dk/FviaDW8LHmK52DlcH4WP2n6gI8vN1aesBFgo9w==",
      "dev": true,
      "dependencies": {
        "yallist": "^3.0.2"
      }
    },
    "node_modules/lzutf8": {
      "version": "0.6.3",
      "resolved": "https://registry.npmjs.org/lzutf8/-/lzutf8-0.6.3.tgz",
      "integrity": "sha512-CAkF9HKrM+XpB0f3DepQ2to2iUEo0zrbh+XgBqgNBc1+k8HMM3u/YSfHI3Dr4GmoTIez2Pr/If1XFl3rU26AwA==",
      "dependencies": {
        "readable-stream": "^4.0.0"
      }
    },
    "node_modules/lzutf8/node_modules/readable-stream": {
      "version": "4.5.2",
      "resolved": "https://registry.npmjs.org/readable-stream/-/readable-stream-4.5.2.tgz",
      "integrity": "sha512-yjavECdqeZ3GLXNgRXgeQEdz9fvDDkNKyHnbHRFtOr7/LcfgBcmct7t/ET+HaCTqfh06OzoAxrkN/IfjJBVe+g==",
      "dependencies": {
        "abort-controller": "^3.0.0",
        "buffer": "^6.0.3",
        "events": "^3.3.0",
        "process": "^0.11.10",
        "string_decoder": "^1.3.0"
      },
      "engines": {
        "node": "^12.22.0 || ^14.17.0 || >=16.0.0"
      }
    },
    "node_modules/map-age-cleaner": {
      "version": "0.1.3",
      "resolved": "https://registry.npmjs.org/map-age-cleaner/-/map-age-cleaner-0.1.3.tgz",
      "integrity": "sha512-bJzx6nMoP6PDLPBFmg7+xRKeFZvFboMrGlxmNj9ClvX53KrmvM5bXFXEWjbz4cz1AFn+jWJ9z/DJSz7hrs0w3w==",
      "dependencies": {
        "p-defer": "^1.0.0"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/map-stream": {
      "version": "0.1.0",
      "resolved": "https://registry.npmjs.org/map-stream/-/map-stream-0.1.0.tgz",
      "integrity": "sha512-CkYQrPYZfWnu/DAmVCpTSX/xHpKZ80eKh2lAkyA6AJTef6bW+6JpbQZN5rofum7da+SyN1bi5ctTm+lTfcCW3g=="
    },
    "node_modules/mem": {
      "version": "4.3.0",
      "resolved": "https://registry.npmjs.org/mem/-/mem-4.3.0.tgz",
      "integrity": "sha512-qX2bG48pTqYRVmDB37rn/6PT7LcR8T7oAX3bf99u1Tt1nzxYfxkgqDwUwolPlXweM0XzBOBFzSx4kfp7KP1s/w==",
      "dependencies": {
        "map-age-cleaner": "^0.1.1",
        "mimic-fn": "^2.0.0",
        "p-is-promise": "^2.0.0"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/mem/node_modules/mimic-fn": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/mimic-fn/-/mimic-fn-2.1.0.tgz",
      "integrity": "sha512-OqbOk5oEQeAZ8WXWydlu9HJjz9WVdEIvamMCcXmuqUYjTknH/sqsWvhQ3vgwKFRR1HpjvNBKQ37nbJgYzGqGcg==",
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/merge-stream": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/merge-stream/-/merge-stream-2.0.0.tgz",
      "integrity": "sha512-abv/qOcuPfk3URPfDzmZU1LKmuw8kT+0nIHvKrKgFrwifol/doWcdA4ZqsWQ8ENrFKkd67Mfpo/LovbIUsbt3w=="
    },
    "node_modules/merge2": {
      "version": "1.4.1",
      "resolved": "https://registry.npmjs.org/merge2/-/merge2-1.4.1.tgz",
      "integrity": "sha512-8q7VEgMJW4J8tcfVPy8g09NcQwZdbwFEqhe/WZkoIzjn/3TGDwtOCYtXGxA3O8tPzpczCCDgv+P2P5y00ZJOOg==",
      "dev": true,
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/micro-ftch": {
      "version": "0.3.1",
      "resolved": "https://registry.npmjs.org/micro-ftch/-/micro-ftch-0.3.1.tgz",
      "integrity": "sha512-/0LLxhzP0tfiR5hcQebtudP56gUurs2CLkGarnCiB/OqEyUFQ6U3paQi/tgLv0hBJYt2rnr9MNpxz4fiiugstg=="
    },
    "node_modules/micromatch": {
      "version": "4.0.8",
      "resolved": "https://registry.npmjs.org/micromatch/-/micromatch-4.0.8.tgz",
      "integrity": "sha512-PXwfBhYu0hBCPw8Dn0E+WDYb7af3dSLVWKi3HGv84IdF4TyFoC0ysxFd0Goxw7nSv4T/PzEJQxsYsEiFCKo2BA==",
      "dependencies": {
        "braces": "^3.0.3",
        "picomatch": "^2.3.1"
      },
      "engines": {
        "node": ">=8.6"
      }
    },
    "node_modules/mime": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/mime/-/mime-3.0.0.tgz",
      "integrity": "sha512-jSCU7/VB1loIWBZe14aEYHU/+1UMEHoaO7qxCOVJOw9GgH72VAWppxNcjU+x9a2k3GSIBXNKxXQFqRvvZ7vr3A==",
      "bin": {
        "mime": "cli.js"
      },
      "engines": {
        "node": ">=10.0.0"
      }
    },
    "node_modules/mime-db": {
      "version": "1.52.0",
      "resolved": "https://registry.npmjs.org/mime-db/-/mime-db-1.52.0.tgz",
      "integrity": "sha512-sPU4uV7dYlvtWJxwwxHD0PuihVNiE7TyAbQ5SWxDCB9mUYvOgroQOwYQQOKPJ8CIbE+1ETVlOoK1UC2nU3gYvg==",
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/mime-types": {
      "version": "2.1.35",
      "resolved": "https://registry.npmjs.org/mime-types/-/mime-types-2.1.35.tgz",
      "integrity": "sha512-ZDY+bPm5zTTF+YpCrAU9nK0UgICYPT0QtT1NZWFv4s++TNkcgVaT0g6+4R2uI4MjQjzysHB1zxuWL50hzaeXiw==",
      "dependencies": {
        "mime-db": "1.52.0"
      },
      "engines": {
        "node": ">= 0.6"
      }
    },
    "node_modules/mimic-fn": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/mimic-fn/-/mimic-fn-4.0.0.tgz",
      "integrity": "sha512-vqiC06CuhBTUdZH+RYl8sFrL096vA45Ok5ISO6sE/Mr1jRbGH4Csnhi8f3wKVl7x8mO4Au7Ir9D3Oyv1VYMFJw==",
      "engines": {
        "node": ">=12"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/minimalistic-assert": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/minimalistic-assert/-/minimalistic-assert-1.0.1.tgz",
      "integrity": "sha512-UtJcAD4yEaGtjPezWuO9wC4nwUnVH/8/Im3yEHQP4b67cXlD/Qr9hdITCU1xDbSEXg2XKNaP8jsReV7vQd00/A=="
    },
    "node_modules/minimalistic-crypto-utils": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/minimalistic-crypto-utils/-/minimalistic-crypto-utils-1.0.1.tgz",
      "integrity": "sha512-JIYlbt6g8i5jKfJ3xz7rF0LXmv2TkDxBLUkiBeZ7bAx4GnnNMr8xFpGnOxn6GhTEHx3SjRrZEoU+j04prX1ktg=="
    },
    "node_modules/minimatch": {
      "version": "9.0.3",
      "resolved": "https://registry.npmjs.org/minimatch/-/minimatch-9.0.3.tgz",
      "integrity": "sha512-RHiac9mvaRw0x3AYRgDC1CxAP7HTcNrrECeA8YYJeWnpo+2Q5CegtZjaotWTWxDG3UeGA1coE05iH1mPjT/2mg==",
      "dev": true,
      "dependencies": {
        "brace-expansion": "^2.0.1"
      },
      "engines": {
        "node": ">=16 || 14 >=14.17"
      },
      "funding": {
        "url": "https://github.com/sponsors/isaacs"
      }
    },
    "node_modules/minimist": {
      "version": "1.2.8",
      "resolved": "https://registry.npmjs.org/minimist/-/minimist-1.2.8.tgz",
      "integrity": "sha512-2yyAR8qBkN3YuheJanUpWC5U3bb5osDywNB8RzDVlDwDHbocAJveqqj1u8+SVD7jkWT4yvsHCpWqqWqAxb0zCA==",
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/minipass": {
      "version": "7.1.2",
      "resolved": "https://registry.npmjs.org/minipass/-/minipass-7.1.2.tgz",
      "integrity": "sha512-qOOzS1cBTWYF4BH8fVePDBOO9iptMnGUEZwNc/cMWnTV2nVLZ7VoNWEPHkYczZA0pdoA7dl6e7FL659nX9S2aw==",
      "dev": true,
      "engines": {
        "node": ">=16 || 14 >=14.17"
      }
    },
    "node_modules/mlly": {
      "version": "1.7.2",
      "resolved": "https://registry.npmjs.org/mlly/-/mlly-1.7.2.tgz",
      "integrity": "sha512-tN3dvVHYVz4DhSXinXIk7u9syPYaJvio118uomkovAtWBT+RdbP6Lfh/5Lvo519YMmwBafwlh20IPTXIStscpA==",
      "dependencies": {
        "acorn": "^8.12.1",
        "pathe": "^1.1.2",
        "pkg-types": "^1.2.0",
        "ufo": "^1.5.4"
      }
    },
    "node_modules/moment": {
      "version": "2.30.1",
      "resolved": "https://registry.npmjs.org/moment/-/moment-2.30.1.tgz",
      "integrity": "sha512-uEmtNhbDOrWPFS+hdjFCBfy9f2YoyzRpwcl+DqpC6taX21FzsTLQVbMV/W7PzNSX6x/bhC1zA3c2UQ5NzH6how==",
      "engines": {
        "node": "*"
      }
    },
    "node_modules/motion": {
      "version": "10.16.2",
      "resolved": "https://registry.npmjs.org/motion/-/motion-10.16.2.tgz",
      "integrity": "sha512-p+PurYqfUdcJZvtnmAqu5fJgV2kR0uLFQuBKtLeFVTrYEVllI99tiOTSefVNYuip9ELTEkepIIDftNdze76NAQ==",
      "dependencies": {
        "@motionone/animation": "^10.15.1",
        "@motionone/dom": "^10.16.2",
        "@motionone/svelte": "^10.16.2",
        "@motionone/types": "^10.15.1",
        "@motionone/utils": "^10.15.1",
        "@motionone/vue": "^10.16.2"
      }
    },
    "node_modules/ms": {
      "version": "2.1.3",
      "resolved": "https://registry.npmjs.org/ms/-/ms-2.1.3.tgz",
      "integrity": "sha512-6FlzubTLZG3J2a/NVCAleEhjzq5oxgHyaCU9yYXvcLsvoVaHJq/s5xXI6/XXP6tz7R9xAOtHnSO/tXtF3WRTlA=="
    },
    "node_modules/multiformats": {
      "version": "9.9.0",
      "resolved": "https://registry.npmjs.org/multiformats/-/multiformats-9.9.0.tgz",
      "integrity": "sha512-HoMUjhH9T8DDBNT+6xzkrd9ga/XiBI4xLr58LJACwK6G3HTOPeMz4nB4KJs33L2BelrIJa7P0VuNaVF3hMYfjg=="
    },
    "node_modules/mz": {
      "version": "2.7.0",
      "resolved": "https://registry.npmjs.org/mz/-/mz-2.7.0.tgz",
      "integrity": "sha512-z81GNO7nnYMEhrGh9LeymoE4+Yr0Wn5McHIZMK5cfQCl+NDX08sCZgUc9/6MHni9IWuFLm1Z3HTCXu2z9fN62Q==",
      "dev": true,
      "dependencies": {
        "any-promise": "^1.0.0",
        "object-assign": "^4.0.1",
        "thenify-all": "^1.0.0"
      }
    },
    "node_modules/nanoid": {
      "version": "3.3.7",
      "resolved": "https://registry.npmjs.org/nanoid/-/nanoid-3.3.7.tgz",
      "integrity": "sha512-eSRppjcPIatRIMC1U6UngP8XFcz8MQWGQdt1MTBQ7NaAmvXDfvNxbvWV3x2y6CdEUciCSsDHDQZbhYaB8QEo2g==",
      "dev": true,
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/ai"
        }
      ],
      "bin": {
        "nanoid": "bin/nanoid.cjs"
      },
      "engines": {
        "node": "^10 || ^12 || ^13.7 || ^14 || >=15.0.1"
      }
    },
    "node_modules/natural-compare": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/natural-compare/-/natural-compare-1.4.0.tgz",
      "integrity": "sha512-OWND8ei3VtNC9h7V60qff3SVobHr996CTwgxubgyQYEpg290h9J0buyECNNJexkFm5sOajh5G116RYA1c8ZMSw==",
      "dev": true
    },
    "node_modules/nice-try": {
      "version": "1.0.5",
      "resolved": "https://registry.npmjs.org/nice-try/-/nice-try-1.0.5.tgz",
      "integrity": "sha512-1nh45deeb5olNY7eX82BkPO7SSxR5SSYJiPTrTdFUVYwAl8CKMA5N9PjTYkHiRjisVcxcQ1HXdLhx2qxxJzLNQ=="
    },
    "node_modules/node-addon-api": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/node-addon-api/-/node-addon-api-2.0.2.tgz",
      "integrity": "sha512-Ntyt4AIXyaLIuMHF6IOoTakB3K+RWxwtsHNRxllEoA6vPwP9o4866g6YWDLUdnucilZhmkxiHwHr11gAENw+QA=="
    },
    "node_modules/node-fetch": {
      "version": "2.7.0",
      "resolved": "https://registry.npmjs.org/node-fetch/-/node-fetch-2.7.0.tgz",
      "integrity": "sha512-c4FRfUm/dbcWZ7U+1Wq0AwCyFL+3nt2bEw05wfxSz+DWpWsitgmSgYmy2dQdWyKC1694ELPqMs/YzUSNozLt8A==",
      "dependencies": {
        "whatwg-url": "^5.0.0"
      },
      "engines": {
        "node": "4.x || >=6.0.0"
      },
      "peerDependencies": {
        "encoding": "^0.1.0"
      },
      "peerDependenciesMeta": {
        "encoding": {
          "optional": true
        }
      }
    },
    "node_modules/node-fetch-native": {
      "version": "1.6.4",
      "resolved": "https://registry.npmjs.org/node-fetch-native/-/node-fetch-native-1.6.4.tgz",
      "integrity": "sha512-IhOigYzAKHd244OC0JIMIUrjzctirCmPkaIfhDeGcEETWof5zKYUW7e7MYvChGWh/4CJeXEgsRyGzuF334rOOQ=="
    },
    "node_modules/node-forge": {
      "version": "1.3.1",
      "resolved": "https://registry.npmjs.org/node-forge/-/node-forge-1.3.1.tgz",
      "integrity": "sha512-dPEtOeMvF9VMcYV/1Wb8CPoVAXtp6MKMlcbAt4ddqmGqUJ6fQZFXkNZNkNlfevtNkGtaSoXf/vNNNSvgrdXwtA==",
      "engines": {
        "node": ">= 6.13.0"
      }
    },
    "node_modules/node-gyp-build": {
      "version": "4.8.2",
      "resolved": "https://registry.npmjs.org/node-gyp-build/-/node-gyp-build-4.8.2.tgz",
      "integrity": "sha512-IRUxE4BVsHWXkV/SFOut4qTlagw2aM8T5/vnTsmrHJvVoKueJHRc/JaFND7QDDc61kLYUJ6qlZM3sqTSyx2dTw==",
      "bin": {
        "node-gyp-build": "bin.js",
        "node-gyp-build-optional": "optional.js",
        "node-gyp-build-test": "build-test.js"
      }
    },
    "node_modules/node-releases": {
      "version": "2.0.18",
      "resolved": "https://registry.npmjs.org/node-releases/-/node-releases-2.0.18.tgz",
      "integrity": "sha512-d9VeXT4SJ7ZeOqGX6R5EM022wpL+eWPooLI+5UpWn2jCT1aosUQEhQP214x33Wkwx3JQMvIm+tIoVOdodFS40g==",
      "dev": true
    },
    "node_modules/normalize-path": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/normalize-path/-/normalize-path-3.0.0.tgz",
      "integrity": "sha512-6eZs5Ls3WtCisHWp9S2GUy8dqkpGi4BVSz3GaqiE6ezub0512ESztXUwUB6C6IKbQkY2Pnb/mD4WYojCRwcwLA==",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/normalize-range": {
      "version": "0.1.2",
      "resolved": "https://registry.npmjs.org/normalize-range/-/normalize-range-0.1.2.tgz",
      "integrity": "sha512-bdok/XvKII3nUpklnV6P2hxtMNrCboOjAcyBuQnWEhO665FwrSNRxU+AqpsyvO6LgGYPspN+lu5CLtw4jPRKNA==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/npm-run-path": {
      "version": "5.3.0",
      "resolved": "https://registry.npmjs.org/npm-run-path/-/npm-run-path-5.3.0.tgz",
      "integrity": "sha512-ppwTtiJZq0O/ai0z7yfudtBpWIoxM8yE6nHi1X47eFR2EWORqfbu6CnPlNsjeN683eT0qG6H/Pyf9fCcvjnnnQ==",
      "dependencies": {
        "path-key": "^4.0.0"
      },
      "engines": {
        "node": "^12.20.0 || ^14.13.1 || >=16.0.0"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/npm-run-path/node_modules/path-key": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/path-key/-/path-key-4.0.0.tgz",
      "integrity": "sha512-haREypq7xkM7ErfgIyA0z+Bj4AGKlMSdlQE2jvJo6huWD1EdkKYV+G/T4nq0YEF2vgTT8kqMFKo1uHn950r4SQ==",
      "engines": {
        "node": ">=12"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/number-is-nan": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/number-is-nan/-/number-is-nan-1.0.1.tgz",
      "integrity": "sha512-4jbtZXNAsfZbAHiiqjLPBiCl16dES1zI4Hpzzxw61Tk+loF+sBDBKx1ICKKKwIqQ7M0mFn1TmkN7euSncWgHiQ==",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/number-to-bn": {
      "version": "1.7.0",
      "resolved": "https://registry.npmjs.org/number-to-bn/-/number-to-bn-1.7.0.tgz",
      "integrity": "sha512-wsJ9gfSz1/s4ZsJN01lyonwuxA1tml6X1yBDnfpMglypcBRFZZkus26EdPSlqS5GJfYddVZa22p3VNb3z5m5Ig==",
      "dependencies": {
        "bn.js": "4.11.6",
        "strip-hex-prefix": "1.0.0"
      },
      "engines": {
        "node": ">=6.5.0",
        "npm": ">=3"
      }
    },
    "node_modules/number-to-bn/node_modules/bn.js": {
      "version": "4.11.6",
      "resolved": "https://registry.npmjs.org/bn.js/-/bn.js-4.11.6.tgz",
      "integrity": "sha512-XWwnNNFCuuSQ0m3r3C4LE3EiORltHd9M05pq6FOlVeiophzRbMo50Sbz1ehl8K3Z+jw9+vmgnXefY1hz8X+2wA=="
    },
    "node_modules/numbro": {
      "version": "2.5.0",
      "resolved": "https://registry.npmjs.org/numbro/-/numbro-2.5.0.tgz",
      "integrity": "sha512-xDcctDimhzko/e+y+Q2/8i3qNC9Svw1QgOkSkQoO0kIPI473tR9QRbo2KP88Ty9p8WbPy+3OpTaAIzehtuHq+A==",
      "dependencies": {
        "bignumber.js": "^8 || ^9"
      },
      "engines": {
        "node": "*"
      }
    },
    "node_modules/object-assign": {
      "version": "4.1.1",
      "resolved": "https://registry.npmjs.org/object-assign/-/object-assign-4.1.1.tgz",
      "integrity": "sha512-rJgTQnkUnH1sFw8yT6VSU3zD3sWmu6sZhIseY8VX+GRu3P6F7Fu+JNDoXfklElbLJSnc3FUQHVe4cU5hj+BcUg==",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/object-hash": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/object-hash/-/object-hash-3.0.0.tgz",
      "integrity": "sha512-RSn9F68PjH9HqtltsSnqYC1XXoWe9Bju5+213R98cNGttag9q9yAOTzdbsqvIa7aNm5WffBZFpWYr2aWrklWAw==",
      "dev": true,
      "engines": {
        "node": ">= 6"
      }
    },
    "node_modules/object-inspect": {
      "version": "1.13.2",
      "resolved": "https://registry.npmjs.org/object-inspect/-/object-inspect-1.13.2.tgz",
      "integrity": "sha512-IRZSRuzJiynemAXPYtPe5BoI/RESNYR7TYm50MC5Mqbd3Jmw5y790sErYw3V6SryFJD64b74qQQs9wn5Bg/k3g==",
      "engines": {
        "node": ">= 0.4"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/ofetch": {
      "version": "1.4.1",
      "resolved": "https://registry.npmjs.org/ofetch/-/ofetch-1.4.1.tgz",
      "integrity": "sha512-QZj2DfGplQAr2oj9KzceK9Hwz6Whxazmn85yYeVuS3u9XTMOGMRx0kO95MQ+vLsj/S/NwBDMMLU5hpxvI6Tklw==",
      "dependencies": {
        "destr": "^2.0.3",
        "node-fetch-native": "^1.6.4",
        "ufo": "^1.5.4"
      }
    },
    "node_modules/ohash": {
      "version": "1.1.4",
      "resolved": "https://registry.npmjs.org/ohash/-/ohash-1.1.4.tgz",
      "integrity": "sha512-FlDryZAahJmEF3VR3w1KogSEdWX3WhA5GPakFx4J81kEAiHyLMpdLLElS8n8dfNadMgAne/MywcvmogzscVt4g=="
    },
    "node_modules/on-exit-leak-free": {
      "version": "0.2.0",
      "resolved": "https://registry.npmjs.org/on-exit-leak-free/-/on-exit-leak-free-0.2.0.tgz",
      "integrity": "sha512-dqaz3u44QbRXQooZLTUKU41ZrzYrcvLISVgbrzbyCMxpmSLJvZ3ZamIJIZ29P6OhZIkNIQKosdeM6t1LYbA9hg=="
    },
    "node_modules/once": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/once/-/once-1.4.0.tgz",
      "integrity": "sha512-lNaJgI+2Q5URQBkccEKHTQOPaXdUxnZZElQTZY0MFUAuaEqe1E+Nyvgdz/aIyNi6Z9MzO5dv1H8n58/GELp3+w==",
      "dependencies": {
        "wrappy": "1"
      }
    },
    "node_modules/onetime": {
      "version": "6.0.0",
      "resolved": "https://registry.npmjs.org/onetime/-/onetime-6.0.0.tgz",
      "integrity": "sha512-1FlR+gjXK7X+AsAHso35MnyN5KqGwJRi/31ft6x0M194ht7S+rWAvd7PHss9xSKMzE0asv1pyIHaJYq+BbacAQ==",
      "dependencies": {
        "mimic-fn": "^4.0.0"
      },
      "engines": {
        "node": ">=12"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/optionator": {
      "version": "0.9.4",
      "resolved": "https://registry.npmjs.org/optionator/-/optionator-0.9.4.tgz",
      "integrity": "sha512-6IpQ7mKUxRcZNLIObR0hz7lxsapSSIYNZJwXPGeF0mTVqGKFIXj1DQcMoT22S3ROcLyY/rz0PWaWZ9ayWmad9g==",
      "dev": true,
      "dependencies": {
        "deep-is": "^0.1.3",
        "fast-levenshtein": "^2.0.6",
        "levn": "^0.4.1",
        "prelude-ls": "^1.2.1",
        "type-check": "^0.4.0",
        "word-wrap": "^1.2.5"
      },
      "engines": {
        "node": ">= 0.8.0"
      }
    },
    "node_modules/os-locale": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/os-locale/-/os-locale-3.1.0.tgz",
      "integrity": "sha512-Z8l3R4wYWM40/52Z+S265okfFj8Kt2cC2MKY+xNi3kFs+XGI7WXu/I309QQQYbRW4ijiZ+yxs9pqEhJh0DqW3Q==",
      "dependencies": {
        "execa": "^1.0.0",
        "lcid": "^2.0.0",
        "mem": "^4.0.0"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/os-locale/node_modules/cross-spawn": {
      "version": "6.0.5",
      "resolved": "https://registry.npmjs.org/cross-spawn/-/cross-spawn-6.0.5.tgz",
      "integrity": "sha512-eTVLrBSt7fjbDygz805pMnstIs2VTBNkRm0qxZd+M7A5XDdxVRWO5MxGBXZhjY4cqLYLdtrGqRf8mBPmzwSpWQ==",
      "dependencies": {
        "nice-try": "^1.0.4",
        "path-key": "^2.0.1",
        "semver": "^5.5.0",
        "shebang-command": "^1.2.0",
        "which": "^1.2.9"
      },
      "engines": {
        "node": ">=4.8"
      }
    },
    "node_modules/os-locale/node_modules/execa": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/execa/-/execa-1.0.0.tgz",
      "integrity": "sha512-adbxcyWV46qiHyvSp50TKt05tB4tK3HcmF7/nxfAdhnox83seTDbwnaqKO4sXRy7roHAIFqJP/Rw/AuEbX61LA==",
      "dependencies": {
        "cross-spawn": "^6.0.0",
        "get-stream": "^4.0.0",
        "is-stream": "^1.1.0",
        "npm-run-path": "^2.0.0",
        "p-finally": "^1.0.0",
        "signal-exit": "^3.0.0",
        "strip-eof": "^1.0.0"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/os-locale/node_modules/get-stream": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/get-stream/-/get-stream-4.1.0.tgz",
      "integrity": "sha512-GMat4EJ5161kIy2HevLlr4luNjBgvmj413KaQA7jt4V8B4RDsfpHk7WQ9GVqfYyyx8OS/L66Kox+rJRNklLK7w==",
      "dependencies": {
        "pump": "^3.0.0"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/os-locale/node_modules/is-stream": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/is-stream/-/is-stream-1.1.0.tgz",
      "integrity": "sha512-uQPm8kcs47jx38atAcWTVxyltQYoPT68y9aWYdV6yWXSyW8mzSat0TL6CiWdZeCdF3KrAvpVtnHbTv4RN+rqdQ==",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/os-locale/node_modules/npm-run-path": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/npm-run-path/-/npm-run-path-2.0.2.tgz",
      "integrity": "sha512-lJxZYlT4DW/bRUtFh1MQIWqmLwQfAxnqWG4HhEdjMlkrJYnJn0Jrr2u3mgxqaWsdiBc76TYkTG/mhrnYTuzfHw==",
      "dependencies": {
        "path-key": "^2.0.0"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/os-locale/node_modules/path-key": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/path-key/-/path-key-2.0.1.tgz",
      "integrity": "sha512-fEHGKCSmUSDPv4uoj8AlD+joPlq3peND+HRYyxFz4KPw4z926S/b8rIuFs2FYJg3BwsxJf6A9/3eIdLaYC+9Dw==",
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/os-locale/node_modules/semver": {
      "version": "5.7.2",
      "resolved": "https://registry.npmjs.org/semver/-/semver-5.7.2.tgz",
      "integrity": "sha512-cBznnQ9KjJqU67B52RMC65CMarK2600WFnbkcaiwWq3xy/5haFJlshgnpjovMVJ+Hff49d8GEn0b87C5pDQ10g==",
      "bin": {
        "semver": "bin/semver"
      }
    },
    "node_modules/os-locale/node_modules/shebang-command": {
      "version": "1.2.0",
      "resolved": "https://registry.npmjs.org/shebang-command/-/shebang-command-1.2.0.tgz",
      "integrity": "sha512-EV3L1+UQWGor21OmnvojK36mhg+TyIKDh3iFBKBohr5xeXIhNBcx8oWdgkTEEQ+BEFFYdLRuqMfd5L84N1V5Vg==",
      "dependencies": {
        "shebang-regex": "^1.0.0"
      },
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/os-locale/node_modules/shebang-regex": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/shebang-regex/-/shebang-regex-1.0.0.tgz",
      "integrity": "sha512-wpoSFAxys6b2a2wHZ1XpDSgD7N9iVjg29Ph9uV/uaP9Ex/KXlkTZTeddxDPSYQpgvzKLGJke2UU0AzoGCjNIvQ==",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/os-locale/node_modules/signal-exit": {
      "version": "3.0.7",
      "resolved": "https://registry.npmjs.org/signal-exit/-/signal-exit-3.0.7.tgz",
      "integrity": "sha512-wnD2ZE+l+SPC/uoS0vXeE9L1+0wuaMqKlfz9AMUo38JsyLSBWSFcHR1Rri62LZc12vLr1gb3jl7iwQhgwpAbGQ=="
    },
    "node_modules/os-locale/node_modules/which": {
      "version": "1.3.1",
      "resolved": "https://registry.npmjs.org/which/-/which-1.3.1.tgz",
      "integrity": "sha512-HxJdYWq1MTIQbJ3nw0cqssHoTNU267KlrDuGZ1WYlxDStUtKUhOaJmh112/TZmHxxUfuJqPXSOm7tDyas0OSIQ==",
      "dependencies": {
        "isexe": "^2.0.0"
      },
      "bin": {
        "which": "bin/which"
      }
    },
    "node_modules/p-defer": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/p-defer/-/p-defer-1.0.0.tgz",
      "integrity": "sha512-wB3wfAxZpk2AzOfUMJNL+d36xothRSyj8EXOa4f6GMqYDN9BJaaSISbsk+wS9abmnebVw95C2Kb5t85UmpCxuw==",
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/p-finally": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/p-finally/-/p-finally-1.0.0.tgz",
      "integrity": "sha512-LICb2p9CB7FS+0eR1oqWnHhp0FljGLZCWBE9aix0Uye9W8LTQPwMTYVGWQWIw9RdQiDg4+epXQODwIYJtSJaow==",
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/p-is-promise": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/p-is-promise/-/p-is-promise-2.1.0.tgz",
      "integrity": "sha512-Y3W0wlRPK8ZMRbNq97l4M5otioeA5lm1z7bkNkxCka8HSPjR0xRWmpCmc9utiaLP9Jb1eD8BgeIxTW4AIF45Pg==",
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/p-limit": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/p-limit/-/p-limit-3.1.0.tgz",
      "integrity": "sha512-TYOanM3wGwNGsZN2cVTYPArw454xnXj5qmWF1bEoAc4+cU/ol7GVh7odevjp1FNHduHc3KZMcFduxU5Xc6uJRQ==",
      "dev": true,
      "dependencies": {
        "yocto-queue": "^0.1.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/p-locate": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/p-locate/-/p-locate-5.0.0.tgz",
      "integrity": "sha512-LaNjtRWUBY++zB5nE/NwcaoMylSPk+S+ZHNB1TzdbMJMny6dynpAGt7X/tl/QYq3TIeE6nxHppbo2LGymrG5Pw==",
      "dev": true,
      "dependencies": {
        "p-limit": "^3.0.2"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/p-try": {
      "version": "2.2.0",
      "resolved": "https://registry.npmjs.org/p-try/-/p-try-2.2.0.tgz",
      "integrity": "sha512-R4nPAVTAU0B9D35/Gk3uJf/7XYbQcyohSKdvAxIRSNghFl4e71hVoGnBNQz9cWaXxO2I10KTC+3jMdvvoKw6dQ==",
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/package-json-from-dist": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/package-json-from-dist/-/package-json-from-dist-1.0.1.tgz",
      "integrity": "sha512-UEZIS3/by4OC8vL3P2dTXRETpebLI2NiI5vIrjaD/5UtrkFX/tNbwjTSRAGC/+7CAo2pIcBaRgWmcBBHcsaCIw==",
      "dev": true
    },
    "node_modules/parent-module": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/parent-module/-/parent-module-1.0.1.tgz",
      "integrity": "sha512-GQ2EWRpQV8/o+Aw8YqtfZZPfNRWZYkbidE9k5rpl/hC3vtHHBfGm2Ifi6qWV+coDGkrUKZAxE3Lot5kcsRlh+g==",
      "dev": true,
      "dependencies": {
        "callsites": "^3.0.0"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/path-exists": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/path-exists/-/path-exists-4.0.0.tgz",
      "integrity": "sha512-ak9Qy5Q7jYb2Wwcey5Fpvg2KoAc/ZIhLSLOSBmRmygPsGwkVVt0fZa0qrtMz+m6tJTAHfZQ8FnmB4MG4LWy7/w==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/path-is-absolute": {
      "version": "1.0.1",
      "resolved": "https://registry.npmjs.org/path-is-absolute/-/path-is-absolute-1.0.1.tgz",
      "integrity": "sha512-AVbw3UJ2e9bq64vSaS9Am0fje1Pa8pbGqTTsmXfaIiMpnr5DlDhfJOuLj9Sf95ZPVDAUerDfEk88MPmPe7UCQg==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/path-key": {
      "version": "3.1.1",
      "resolved": "https://registry.npmjs.org/path-key/-/path-key-3.1.1.tgz",
      "integrity": "sha512-ojmeN0qd+y0jszEtoY48r0Peq5dwMEkIlCOu6Q5f41lfkswXuKtYrhgoTpLnyIcHm24Uhqx+5Tqm2InSwLhE6Q==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/path-parse": {
      "version": "1.0.7",
      "resolved": "https://registry.npmjs.org/path-parse/-/path-parse-1.0.7.tgz",
      "integrity": "sha512-LDJzPVEEEPR+y48z93A0Ed0yXb8pAByGWo/k5YYdYgpY2/2EsOsksJrq7lOHxryrVOn1ejG6oAp8ahvOIQD8sw==",
      "dev": true
    },
    "node_modules/path-scurry": {
      "version": "1.11.1",
      "resolved": "https://registry.npmjs.org/path-scurry/-/path-scurry-1.11.1.tgz",
      "integrity": "sha512-Xa4Nw17FS9ApQFJ9umLiJS4orGjm7ZzwUrwamcGQuHSzDyth9boKDaycYdDcZDuqYATXw4HFXgaqWTctW/v1HA==",
      "dev": true,
      "dependencies": {
        "lru-cache": "^10.2.0",
        "minipass": "^5.0.0 || ^6.0.2 || ^7.0.0"
      },
      "engines": {
        "node": ">=16 || 14 >=14.18"
      },
      "funding": {
        "url": "https://github.com/sponsors/isaacs"
      }
    },
    "node_modules/path-scurry/node_modules/lru-cache": {
      "version": "10.4.3",
      "resolved": "https://registry.npmjs.org/lru-cache/-/lru-cache-10.4.3.tgz",
      "integrity": "sha512-JNAzZcXrCt42VGLuYz0zfAzDfAvJWW6AfYlDBQyDV5DClI2m5sAmK+OIO7s59XfsRsWHp02jAJrRadPRGTt6SQ==",
      "dev": true
    },
    "node_modules/path-type": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/path-type/-/path-type-4.0.0.tgz",
      "integrity": "sha512-gDKb8aZMDeD/tZWs9P6+q0J9Mwkdl6xMV8TjnGP3qJVJ06bdMgkbBlLU8IdfOsIsFz2BW1rNVT3XuNEl8zPAvw==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/pathe": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/pathe/-/pathe-1.1.2.tgz",
      "integrity": "sha512-whLdWMYL2TwI08hn8/ZqAbrVemu0LNaNNJZX73O6qaIdCTfXutsLhMkjdENX0qhsQ9uIimo4/aQOmXkoon2nDQ=="
    },
    "node_modules/pause-stream": {
      "version": "0.0.11",
      "resolved": "https://registry.npmjs.org/pause-stream/-/pause-stream-0.0.11.tgz",
      "integrity": "sha512-e3FBlXLmN/D1S+zHzanP4E/4Z60oFAa3O051qt1pxa7DEJWKAyil6upYVXCWadEnuoqa4Pkc9oUx9zsxYeRv8A==",
      "dependencies": {
        "through": "~2.3"
      }
    },
    "node_modules/picocolors": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/picocolors/-/picocolors-1.1.1.tgz",
      "integrity": "sha512-xceH2snhtb5M9liqDsmEw56le376mTZkEX/jEb/RxNFyegNul7eNslCXP9FDj/Lcu0X8KEyMceP2ntpaHrDEVA==",
      "dev": true
    },
    "node_modules/picomatch": {
      "version": "2.3.1",
      "resolved": "https://registry.npmjs.org/picomatch/-/picomatch-2.3.1.tgz",
      "integrity": "sha512-JU3teHTNjmE2VCGFzuY8EXzCDVwEqB2a8fsIvwaStHhAWJEeVd1o1QD80CU6+ZdEXXSLbSsuLwJjkCBWqRQUVA==",
      "engines": {
        "node": ">=8.6"
      },
      "funding": {
        "url": "https://github.com/sponsors/jonschlinkert"
      }
    },
    "node_modules/pify": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/pify/-/pify-3.0.0.tgz",
      "integrity": "sha512-C3FsVNH1udSEX48gGX1xfvwTWfsYWj5U+8/uK15BGzIGrKoUpghX8hWZwa/OFnakBiiVNmBvemTJR5mcy7iPcg==",
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/pino": {
      "version": "7.11.0",
      "resolved": "https://registry.npmjs.org/pino/-/pino-7.11.0.tgz",
      "integrity": "sha512-dMACeu63HtRLmCG8VKdy4cShCPKaYDR4youZqoSWLxl5Gu99HUw8bw75thbPv9Nip+H+QYX8o3ZJbTdVZZ2TVg==",
      "dependencies": {
        "atomic-sleep": "^1.0.0",
        "fast-redact": "^3.0.0",
        "on-exit-leak-free": "^0.2.0",
        "pino-abstract-transport": "v0.5.0",
        "pino-std-serializers": "^4.0.0",
        "process-warning": "^1.0.0",
        "quick-format-unescaped": "^4.0.3",
        "real-require": "^0.1.0",
        "safe-stable-stringify": "^2.1.0",
        "sonic-boom": "^2.2.1",
        "thread-stream": "^0.15.1"
      },
      "bin": {
        "pino": "bin.js"
      }
    },
    "node_modules/pino-abstract-transport": {
      "version": "0.5.0",
      "resolved": "https://registry.npmjs.org/pino-abstract-transport/-/pino-abstract-transport-0.5.0.tgz",
      "integrity": "sha512-+KAgmVeqXYbTtU2FScx1XS3kNyfZ5TrXY07V96QnUSFqo2gAqlvmaxH67Lj7SWazqsMabf+58ctdTcBgnOLUOQ==",
      "dependencies": {
        "duplexify": "^4.1.2",
        "split2": "^4.0.0"
      }
    },
    "node_modules/pino-std-serializers": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/pino-std-serializers/-/pino-std-serializers-4.0.0.tgz",
      "integrity": "sha512-cK0pekc1Kjy5w9V2/n+8MkZwusa6EyyxfeQCB799CQRhRt/CqYKiWs5adeu8Shve2ZNffvfC/7J64A2PJo1W/Q=="
    },
    "node_modules/pirates": {
      "version": "4.0.6",
      "resolved": "https://registry.npmjs.org/pirates/-/pirates-4.0.6.tgz",
      "integrity": "sha512-saLsH7WeYYPiD25LDuLRRY/i+6HaPYr6G1OUlN39otzkSTxKnubR9RTxS3/Kk50s1g2JTgFwWQDQyplC5/SHZg==",
      "dev": true,
      "engines": {
        "node": ">= 6"
      }
    },
    "node_modules/pkg-types": {
      "version": "1.2.1",
      "resolved": "https://registry.npmjs.org/pkg-types/-/pkg-types-1.2.1.tgz",
      "integrity": "sha512-sQoqa8alT3nHjGuTjuKgOnvjo4cljkufdtLMnO2LBP/wRwuDlo1tkaEdMxCRhyGRPacv/ztlZgDPm2b7FAmEvw==",
      "dependencies": {
        "confbox": "^0.1.8",
        "mlly": "^1.7.2",
        "pathe": "^1.1.2"
      }
    },
    "node_modules/pngjs": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/pngjs/-/pngjs-5.0.0.tgz",
      "integrity": "sha512-40QW5YalBNfQo5yRYmiw7Yz6TKKVr3h6970B2YE+3fQpsWcrbj1PzJgxeJ19DRQjhMbKPIuMY8rFaXc8moolVw==",
      "engines": {
        "node": ">=10.13.0"
      }
    },
    "node_modules/pony-cause": {
      "version": "2.1.11",
      "resolved": "https://registry.npmjs.org/pony-cause/-/pony-cause-2.1.11.tgz",
      "integrity": "sha512-M7LhCsdNbNgiLYiP4WjsfLUuFmCfnjdF6jKe2R9NKl4WFN+HZPGHJZ9lnLP7f9ZnKe3U9nuWD0szirmj+migUg==",
      "engines": {
        "node": ">=12.0.0"
      }
    },
    "node_modules/postcss": {
      "version": "8.4.47",
      "resolved": "https://registry.npmjs.org/postcss/-/postcss-8.4.47.tgz",
      "integrity": "sha512-56rxCq7G/XfB4EkXq9Egn5GCqugWvDFjafDOThIdMBsI15iqPqR5r15TfSr1YPYeEI19YeaXMCbY6u88Y76GLQ==",
      "dev": true,
      "funding": [
        {
          "type": "opencollective",
          "url": "https://opencollective.com/postcss/"
        },
        {
          "type": "tidelift",
          "url": "https://tidelift.com/funding/github/npm/postcss"
        },
        {
          "type": "github",
          "url": "https://github.com/sponsors/ai"
        }
      ],
      "dependencies": {
        "nanoid": "^3.3.7",
        "picocolors": "^1.1.0",
        "source-map-js": "^1.2.1"
      },
      "engines": {
        "node": "^10 || ^12 || >=14"
      }
    },
    "node_modules/postcss-import": {
      "version": "15.1.0",
      "resolved": "https://registry.npmjs.org/postcss-import/-/postcss-import-15.1.0.tgz",
      "integrity": "sha512-hpr+J05B2FVYUAXHeK1YyI267J/dDDhMU6B6civm8hSY1jYJnBXxzKDKDswzJmtLHryrjhnDjqqp/49t8FALew==",
      "dev": true,
      "dependencies": {
        "postcss-value-parser": "^4.0.0",
        "read-cache": "^1.0.0",
        "resolve": "^1.1.7"
      },
      "engines": {
        "node": ">=14.0.0"
      },
      "peerDependencies": {
        "postcss": "^8.0.0"
      }
    },
    "node_modules/postcss-js": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/postcss-js/-/postcss-js-4.0.1.tgz",
      "integrity": "sha512-dDLF8pEO191hJMtlHFPRa8xsizHaM82MLfNkUHdUtVEV3tgTp5oj+8qbEqYM57SLfc74KSbw//4SeJma2LRVIw==",
      "dev": true,
      "dependencies": {
        "camelcase-css": "^2.0.1"
      },
      "engines": {
        "node": "^12 || ^14 || >= 16"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/postcss/"
      },
      "peerDependencies": {
        "postcss": "^8.4.21"
      }
    },
    "node_modules/postcss-load-config": {
      "version": "4.0.2",
      "resolved": "https://registry.npmjs.org/postcss-load-config/-/postcss-load-config-4.0.2.tgz",
      "integrity": "sha512-bSVhyJGL00wMVoPUzAVAnbEoWyqRxkjv64tUl427SKnPrENtq6hJwUojroMz2VB+Q1edmi4IfrAPpami5VVgMQ==",
      "dev": true,
      "funding": [
        {
          "type": "opencollective",
          "url": "https://opencollective.com/postcss/"
        },
        {
          "type": "github",
          "url": "https://github.com/sponsors/ai"
        }
      ],
      "dependencies": {
        "lilconfig": "^3.0.0",
        "yaml": "^2.3.4"
      },
      "engines": {
        "node": ">= 14"
      },
      "peerDependencies": {
        "postcss": ">=8.0.9",
        "ts-node": ">=9.0.0"
      },
      "peerDependenciesMeta": {
        "postcss": {
          "optional": true
        },
        "ts-node": {
          "optional": true
        }
      }
    },
    "node_modules/postcss-load-config/node_modules/lilconfig": {
      "version": "3.1.2",
      "resolved": "https://registry.npmjs.org/lilconfig/-/lilconfig-3.1.2.tgz",
      "integrity": "sha512-eop+wDAvpItUys0FWkHIKeC9ybYrTGbU41U5K7+bttZZeohvnY7M9dZ5kB21GNWiFT2q1OoPTvncPCgSOVO5ow==",
      "dev": true,
      "engines": {
        "node": ">=14"
      },
      "funding": {
        "url": "https://github.com/sponsors/antonk52"
      }
    },
    "node_modules/postcss-nested": {
      "version": "6.2.0",
      "resolved": "https://registry.npmjs.org/postcss-nested/-/postcss-nested-6.2.0.tgz",
      "integrity": "sha512-HQbt28KulC5AJzG+cZtj9kvKB93CFCdLvog1WFLf1D+xmMvPGlBstkpTEZfK5+AN9hfJocyBFCNiqyS48bpgzQ==",
      "dev": true,
      "funding": [
        {
          "type": "opencollective",
          "url": "https://opencollective.com/postcss/"
        },
        {
          "type": "github",
          "url": "https://github.com/sponsors/ai"
        }
      ],
      "dependencies": {
        "postcss-selector-parser": "^6.1.1"
      },
      "engines": {
        "node": ">=12.0"
      },
      "peerDependencies": {
        "postcss": "^8.2.14"
      }
    },
    "node_modules/postcss-selector-parser": {
      "version": "6.1.2",
      "resolved": "https://registry.npmjs.org/postcss-selector-parser/-/postcss-selector-parser-6.1.2.tgz",
      "integrity": "sha512-Q8qQfPiZ+THO/3ZrOrO0cJJKfpYCagtMUkXbnEfmgUjwXg6z/WBeOyS9APBBPCTSiDV+s4SwQGu8yFsiMRIudg==",
      "dev": true,
      "dependencies": {
        "cssesc": "^3.0.0",
        "util-deprecate": "^1.0.2"
      },
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/postcss-value-parser": {
      "version": "4.2.0",
      "resolved": "https://registry.npmjs.org/postcss-value-parser/-/postcss-value-parser-4.2.0.tgz",
      "integrity": "sha512-1NNCs6uurfkVbeXG4S8JFT9t19m45ICnif8zWLd5oPSZ50QnwMfK+H3jv408d4jw/7Bttv5axS5IiHoLaVNHeQ==",
      "dev": true
    },
    "node_modules/preact": {
      "version": "10.24.3",
      "resolved": "https://registry.npmjs.org/preact/-/preact-10.24.3.tgz",
      "integrity": "sha512-Z2dPnBnMUfyQfSQ+GBdsGa16hz35YmLmtTLhM169uW944hYL6xzTYkJjC07j+Wosz733pMWx0fgON3JNw1jJQA==",
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/preact"
      }
    },
    "node_modules/prelude-ls": {
      "version": "1.2.1",
      "resolved": "https://registry.npmjs.org/prelude-ls/-/prelude-ls-1.2.1.tgz",
      "integrity": "sha512-vkcDPrRZo1QZLbn5RLGPpg/WmIQ65qoWWhcGKf/b5eplkkarX0m9z8ppCat4mlOqUsWpyNuYgO3VRyrYHSzX5g==",
      "dev": true,
      "engines": {
        "node": ">= 0.8.0"
      }
    },
    "node_modules/process": {
      "version": "0.11.10",
      "resolved": "https://registry.npmjs.org/process/-/process-0.11.10.tgz",
      "integrity": "sha512-cdGef/drWFoydD1JsMzuFf8100nZl+GT+yacc2bEced5f9Rjk4z+WtFUTBu9PhOi9j/jfmBPu0mMEY4wIdAF8A==",
      "engines": {
        "node": ">= 0.6.0"
      }
    },
    "node_modules/process-warning": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/process-warning/-/process-warning-1.0.0.tgz",
      "integrity": "sha512-du4wfLyj4yCZq1VupnVSZmRsPJsNuxoDQFdCFHLaYiEbFBD7QE0a+I4D7hOxrVnh78QE/YipFAj9lXHiXocV+Q=="
    },
    "node_modules/prop-types": {
      "version": "15.8.1",
      "resolved": "https://registry.npmjs.org/prop-types/-/prop-types-15.8.1.tgz",
      "integrity": "sha512-oj87CgZICdulUohogVAR7AjlC0327U4el4L6eAvOqCeudMDVU0NThNaV+b9Df4dXgSP1gXMTnPdhfe/2qDH5cg==",
      "dependencies": {
        "loose-envify": "^1.4.0",
        "object-assign": "^4.1.1",
        "react-is": "^16.13.1"
      }
    },
    "node_modules/proxy-compare": {
      "version": "2.5.1",
      "resolved": "https://registry.npmjs.org/proxy-compare/-/proxy-compare-2.5.1.tgz",
      "integrity": "sha512-oyfc0Tx87Cpwva5ZXezSp5V9vht1c7dZBhvuV/y3ctkgMVUmiAGDVeeB0dKhGSyT0v1ZTEQYpe/RXlBVBNuCLA=="
    },
    "node_modules/proxy-from-env": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/proxy-from-env/-/proxy-from-env-1.1.0.tgz",
      "integrity": "sha512-D+zkORCbA9f1tdWRK0RaCR3GPv50cMxcrz4X8k5LTSUD1Dkw47mKJEZQNunItRTkWwgtaUSo1RVFRIG9ZXiFYg=="
    },
    "node_modules/ps-tree": {
      "version": "1.2.0",
      "resolved": "https://registry.npmjs.org/ps-tree/-/ps-tree-1.2.0.tgz",
      "integrity": "sha512-0VnamPPYHl4uaU/nSFeZZpR21QAWRz+sRv4iW9+v/GS/J5U5iZB5BNN6J0RMoOvdx2gWM2+ZFMIm58q24e4UYA==",
      "dependencies": {
        "event-stream": "=3.3.4"
      },
      "bin": {
        "ps-tree": "bin/ps-tree.js"
      },
      "engines": {
        "node": ">= 0.10"
      }
    },
    "node_modules/pseudomap": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/pseudomap/-/pseudomap-1.0.2.tgz",
      "integrity": "sha512-b/YwNhb8lk1Zz2+bXXpS/LK9OisiZZ1SNsSLxN1x2OXVEhW2Ckr/7mWE5vrC1ZTiJlD9g19jWszTmJsB+oEpFQ=="
    },
    "node_modules/pump": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/pump/-/pump-3.0.2.tgz",
      "integrity": "sha512-tUPXtzlGM8FE3P0ZL6DVs/3P58k9nk8/jZeQCurTJylQA8qFYzHFfhBJkuqyE0FifOsQ0uKWekiZ5g8wtr28cw==",
      "dependencies": {
        "end-of-stream": "^1.1.0",
        "once": "^1.3.1"
      }
    },
    "node_modules/punycode": {
      "version": "2.3.1",
      "resolved": "https://registry.npmjs.org/punycode/-/punycode-2.3.1.tgz",
      "integrity": "sha512-vYt7UD1U9Wg6138shLtLOvdAu+8DsC/ilFtEVHcH+wydcSpNE20AfSOduf6MkRFahL5FY7X1oU7nKVZFtfq8Fg==",
      "dev": true,
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/qrcode": {
      "version": "1.5.4",
      "resolved": "https://registry.npmjs.org/qrcode/-/qrcode-1.5.4.tgz",
      "integrity": "sha512-1ca71Zgiu6ORjHqFBDpnSMTR2ReToX4l1Au1VFLyVeBTFavzQnv5JxMFr3ukHVKpSrSA2MCk0lNJSykjUfz7Zg==",
      "dependencies": {
        "dijkstrajs": "^1.0.1",
        "pngjs": "^5.0.0",
        "yargs": "^15.3.1"
      },
      "bin": {
        "qrcode": "bin/qrcode"
      },
      "engines": {
        "node": ">=10.13.0"
      }
    },
    "node_modules/qs": {
      "version": "6.13.0",
      "resolved": "https://registry.npmjs.org/qs/-/qs-6.13.0.tgz",
      "integrity": "sha512-+38qI9SOr8tfZ4QmJNplMUxqjbe7LKvvZgWdExBOmd+egZTtjLB67Gu0HRX3u/XOq7UU2Nx6nsjvS16Z9uwfpg==",
      "dependencies": {
        "side-channel": "^1.0.6"
      },
      "engines": {
        "node": ">=0.6"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/query-string": {
      "version": "7.1.3",
      "resolved": "https://registry.npmjs.org/query-string/-/query-string-7.1.3.tgz",
      "integrity": "sha512-hh2WYhq4fi8+b+/2Kg9CEge4fDPvHS534aOOvOZeQ3+Vf2mCFsaFBYj0i+iXcAq6I9Vzp5fjMFBlONvayDC1qg==",
      "dependencies": {
        "decode-uri-component": "^0.2.2",
        "filter-obj": "^1.1.0",
        "split-on-first": "^1.0.0",
        "strict-uri-encode": "^2.0.0"
      },
      "engines": {
        "node": ">=6"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/queue-microtask": {
      "version": "1.2.3",
      "resolved": "https://registry.npmjs.org/queue-microtask/-/queue-microtask-1.2.3.tgz",
      "integrity": "sha512-NuaNSa6flKT5JaSYQzJok04JzTL1CA6aGhv5rfLW3PgqA+M2ChpZQnAC8h8i4ZFkBS8X5RqkDBHA7r4hej3K9A==",
      "dev": true,
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/feross"
        },
        {
          "type": "patreon",
          "url": "https://www.patreon.com/feross"
        },
        {
          "type": "consulting",
          "url": "https://feross.org/support"
        }
      ]
    },
    "node_modules/quick-format-unescaped": {
      "version": "4.0.4",
      "resolved": "https://registry.npmjs.org/quick-format-unescaped/-/quick-format-unescaped-4.0.4.tgz",
      "integrity": "sha512-tYC1Q1hgyRuHgloV/YXs2w15unPVh8qfu/qCTfhTYamaw7fyhumKa2yGpdSo87vY32rIclj+4fWYQXUMs9EHvg=="
    },
    "node_modules/radix3": {
      "version": "1.1.2",
      "resolved": "https://registry.npmjs.org/radix3/-/radix3-1.1.2.tgz",
      "integrity": "sha512-b484I/7b8rDEdSDKckSSBA8knMpcdsXudlE/LNL639wFoHKwLbEkQFZHWEYwDC0wa0FKUcCY+GAF73Z7wxNVFA=="
    },
    "node_modules/rc-align": {
      "version": "4.0.15",
      "resolved": "https://registry.npmjs.org/rc-align/-/rc-align-4.0.15.tgz",
      "integrity": "sha512-wqJtVH60pka/nOX7/IspElA8gjPNQKIx/ZqJ6heATCkXpe1Zg4cPVrMD2vC96wjsFFL8WsmhPbx9tdMo1qqlIA==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "2.x",
        "dom-align": "^1.7.0",
        "rc-util": "^5.26.0",
        "resize-observer-polyfill": "^1.5.1"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-cascader": {
      "version": "3.7.3",
      "resolved": "https://registry.npmjs.org/rc-cascader/-/rc-cascader-3.7.3.tgz",
      "integrity": "sha512-KBpT+kzhxDW+hxPiNk4zaKa99+Lie2/8nnI11XF+FIOPl4Bj9VlFZi61GrnWzhLGA7VEN+dTxAkNOjkySDa0dA==",
      "dependencies": {
        "@babel/runtime": "^7.12.5",
        "array-tree-filter": "^2.1.0",
        "classnames": "^2.3.1",
        "rc-select": "~14.1.0",
        "rc-tree": "~5.7.0",
        "rc-util": "^5.6.1"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-checkbox": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/rc-checkbox/-/rc-checkbox-3.0.1.tgz",
      "integrity": "sha512-k7nxDWxYF+jDI0ZcCvuvj71xONmWRVe5+1MKcERRR9MRyP3tZ69b+yUCSXXh+sik4/Hc9P5wHr2nnUoGS2zBjA==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "^2.3.2",
        "rc-util": "^5.25.2"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-collapse": {
      "version": "3.4.2",
      "resolved": "https://registry.npmjs.org/rc-collapse/-/rc-collapse-3.4.2.tgz",
      "integrity": "sha512-jpTwLgJzkhAgp2Wpi3xmbTbbYExg6fkptL67Uu5LCRVEj6wqmy0DHTjjeynsjOLsppHGHu41t1ELntZ0lEvS/Q==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "2.x",
        "rc-motion": "^2.3.4",
        "rc-util": "^5.2.1",
        "shallowequal": "^1.1.0"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-dialog": {
      "version": "9.0.4",
      "resolved": "https://registry.npmjs.org/rc-dialog/-/rc-dialog-9.0.4.tgz",
      "integrity": "sha512-pmnPRZKd9CGzGgf4a1ysBvMhxm8Afx5fF6M7AzLtJ0qh8X1bshurDlqnK4MBNAB4hAeAMMbz6Ytb1rkGMvKFbQ==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "@rc-component/portal": "^1.0.0-8",
        "classnames": "^2.2.6",
        "rc-motion": "^2.3.0",
        "rc-util": "^5.21.0"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-drawer": {
      "version": "6.3.0",
      "resolved": "https://registry.npmjs.org/rc-drawer/-/rc-drawer-6.3.0.tgz",
      "integrity": "sha512-uBZVb3xTAR+dBV53d/bUhTctCw3pwcwJoM7g5aX+7vgwt2zzVzoJ6aqFjYJpBlZ9zp0dVYN8fV+hykFE7c4lig==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "@rc-component/portal": "^1.1.1",
        "classnames": "^2.2.6",
        "rc-motion": "^2.6.1",
        "rc-util": "^5.21.2"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-dropdown": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/rc-dropdown/-/rc-dropdown-4.0.1.tgz",
      "integrity": "sha512-OdpXuOcme1rm45cR0Jzgfl1otzmU4vuBVb+etXM8vcaULGokAKVpKlw8p6xzspG7jGd/XxShvq+N3VNEfk/l5g==",
      "dependencies": {
        "@babel/runtime": "^7.18.3",
        "classnames": "^2.2.6",
        "rc-trigger": "^5.3.1",
        "rc-util": "^5.17.0"
      },
      "peerDependencies": {
        "react": ">=16.11.0",
        "react-dom": ">=16.11.0"
      }
    },
    "node_modules/rc-field-form": {
      "version": "1.38.2",
      "resolved": "https://registry.npmjs.org/rc-field-form/-/rc-field-form-1.38.2.tgz",
      "integrity": "sha512-O83Oi1qPyEv31Sg+Jwvsj6pXc8uQI2BtIAkURr5lvEYHVggXJhdU/nynK8wY1gbw0qR48k731sN5ON4egRCROA==",
      "dependencies": {
        "@babel/runtime": "^7.18.0",
        "async-validator": "^4.1.0",
        "rc-util": "^5.32.2"
      },
      "engines": {
        "node": ">=8.x"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-image": {
      "version": "5.13.0",
      "resolved": "https://registry.npmjs.org/rc-image/-/rc-image-5.13.0.tgz",
      "integrity": "sha512-iZTOmw5eWo2+gcrJMMcnd7SsxVHl3w5xlyCgsULUdJhJbnuI8i/AL0tVOsE7aLn9VfOh1qgDT3mC2G75/c7mqg==",
      "dependencies": {
        "@babel/runtime": "^7.11.2",
        "@rc-component/portal": "^1.0.2",
        "classnames": "^2.2.6",
        "rc-dialog": "~9.0.0",
        "rc-motion": "^2.6.2",
        "rc-util": "^5.0.6"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-input": {
      "version": "0.1.4",
      "resolved": "https://registry.npmjs.org/rc-input/-/rc-input-0.1.4.tgz",
      "integrity": "sha512-FqDdNz+fV2dKNgfXzcSLKvC+jEs1709t7nD+WdfjrdSaOcefpgc7BUJYadc3usaING+b7ediMTfKxuJBsEFbXA==",
      "dependencies": {
        "@babel/runtime": "^7.11.1",
        "classnames": "^2.2.1",
        "rc-util": "^5.18.1"
      },
      "peerDependencies": {
        "react": ">=16.0.0",
        "react-dom": ">=16.0.0"
      }
    },
    "node_modules/rc-input-number": {
      "version": "7.3.11",
      "resolved": "https://registry.npmjs.org/rc-input-number/-/rc-input-number-7.3.11.tgz",
      "integrity": "sha512-aMWPEjFeles6PQnMqP5eWpxzsvHm9rh1jQOWXExUEIxhX62Fyl/ptifLHOn17+waDG1T/YUb6flfJbvwRhHrbA==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "^2.2.5",
        "rc-util": "^5.23.0"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-mentions": {
      "version": "1.13.1",
      "resolved": "https://registry.npmjs.org/rc-mentions/-/rc-mentions-1.13.1.tgz",
      "integrity": "sha512-FCkaWw6JQygtOz0+Vxz/M/NWqrWHB9LwqlY2RtcuFqWJNFK9njijOOzTSsBGANliGufVUzx/xuPHmZPBV0+Hgw==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "^2.2.6",
        "rc-menu": "~9.8.0",
        "rc-textarea": "^0.4.0",
        "rc-trigger": "^5.0.4",
        "rc-util": "^5.22.5"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-menu": {
      "version": "9.8.4",
      "resolved": "https://registry.npmjs.org/rc-menu/-/rc-menu-9.8.4.tgz",
      "integrity": "sha512-lmw2j8I2fhdIzHmC9ajfImfckt0WDb2KVJJBBRIsxPEw2kGkEfjLMUoB1NgiNT/Q5cC8PdjGOGQjHJIJMwyNMw==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "2.x",
        "rc-motion": "^2.4.3",
        "rc-overflow": "^1.2.8",
        "rc-trigger": "^5.1.2",
        "rc-util": "^5.27.0"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-motion": {
      "version": "2.9.3",
      "resolved": "https://registry.npmjs.org/rc-motion/-/rc-motion-2.9.3.tgz",
      "integrity": "sha512-rkW47ABVkic7WEB0EKJqzySpvDqwl60/tdkY7hWP7dYnh5pm0SzJpo54oW3TDUGXV5wfxXFmMkxrzRRbotQ0+w==",
      "dependencies": {
        "@babel/runtime": "^7.11.1",
        "classnames": "^2.2.1",
        "rc-util": "^5.43.0"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-notification": {
      "version": "4.6.1",
      "resolved": "https://registry.npmjs.org/rc-notification/-/rc-notification-4.6.1.tgz",
      "integrity": "sha512-NSmFYwrrdY3+un1GvDAJQw62Xi9LNMSsoQyo95tuaYrcad5Bn9gJUL8AREufRxSQAQnr64u3LtP3EUyLYT6bhw==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "2.x",
        "rc-motion": "^2.2.0",
        "rc-util": "^5.20.1"
      },
      "engines": {
        "node": ">=8.x"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-overflow": {
      "version": "1.3.2",
      "resolved": "https://registry.npmjs.org/rc-overflow/-/rc-overflow-1.3.2.tgz",
      "integrity": "sha512-nsUm78jkYAoPygDAcGZeC2VwIg/IBGSodtOY3pMof4W3M9qRJgqaDYm03ZayHlde3I6ipliAxbN0RUcGf5KOzw==",
      "dependencies": {
        "@babel/runtime": "^7.11.1",
        "classnames": "^2.2.1",
        "rc-resize-observer": "^1.0.0",
        "rc-util": "^5.37.0"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-pagination": {
      "version": "3.2.0",
      "resolved": "https://registry.npmjs.org/rc-pagination/-/rc-pagination-3.2.0.tgz",
      "integrity": "sha512-5tIXjB670WwwcAJzAqp2J+cOBS9W3cH/WU1EiYwXljuZ4vtZXKlY2Idq8FZrnYBz8KhN3vwPo9CoV/SJS6SL1w==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "^2.2.1"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-picker": {
      "version": "2.7.6",
      "resolved": "https://registry.npmjs.org/rc-picker/-/rc-picker-2.7.6.tgz",
      "integrity": "sha512-H9if/BUJUZBOhPfWcPeT15JUI3/ntrG9muzERrXDkSoWmDj4yzmBvumozpxYrHwjcKnjyDGAke68d+whWwvhHA==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "^2.2.1",
        "date-fns": "2.x",
        "dayjs": "1.x",
        "moment": "^2.24.0",
        "rc-trigger": "^5.0.4",
        "rc-util": "^5.37.0",
        "shallowequal": "^1.1.0"
      },
      "engines": {
        "node": ">=8.x"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-progress": {
      "version": "3.4.2",
      "resolved": "https://registry.npmjs.org/rc-progress/-/rc-progress-3.4.2.tgz",
      "integrity": "sha512-iAGhwWU+tsayP+Jkl9T4+6rHeQTG9kDz8JAHZk4XtQOcYN5fj9H34NXNEdRdZx94VUDHMqCb1yOIvi8eJRh67w==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "^2.2.6",
        "rc-util": "^5.16.1"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-rate": {
      "version": "2.9.3",
      "resolved": "https://registry.npmjs.org/rc-rate/-/rc-rate-2.9.3.tgz",
      "integrity": "sha512-2THssUSnRhtqIouQIIXqsZGzRczvp4WsH4WvGuhiwm+LG2fVpDUJliP9O1zeDOZvYfBE/Bup4SgHun/eCkbjgQ==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "^2.2.5",
        "rc-util": "^5.0.1"
      },
      "engines": {
        "node": ">=8.x"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-resize-observer": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/rc-resize-observer/-/rc-resize-observer-1.4.0.tgz",
      "integrity": "sha512-PnMVyRid9JLxFavTjeDXEXo65HCRqbmLBw9xX9gfC4BZiSzbLXKzW3jPz+J0P71pLbD5tBMTT+mkstV5gD0c9Q==",
      "dependencies": {
        "@babel/runtime": "^7.20.7",
        "classnames": "^2.2.1",
        "rc-util": "^5.38.0",
        "resize-observer-polyfill": "^1.5.1"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-segmented": {
      "version": "2.3.0",
      "resolved": "https://registry.npmjs.org/rc-segmented/-/rc-segmented-2.3.0.tgz",
      "integrity": "sha512-I3FtM5Smua/ESXutFfb8gJ8ZPcvFR+qUgeeGFQHBOvRiRKyAk4aBE5nfqrxXx+h8/vn60DQjOt6i4RNtrbOobg==",
      "dependencies": {
        "@babel/runtime": "^7.11.1",
        "classnames": "^2.2.1",
        "rc-motion": "^2.4.4",
        "rc-util": "^5.17.0"
      },
      "peerDependencies": {
        "react": ">=16.0.0",
        "react-dom": ">=16.0.0"
      }
    },
    "node_modules/rc-select": {
      "version": "14.1.18",
      "resolved": "https://registry.npmjs.org/rc-select/-/rc-select-14.1.18.tgz",
      "integrity": "sha512-4JgY3oG2Yz68ECMUSCON7mtxuJvCSj+LJpHEg/AONaaVBxIIrmI/ZTuMJkyojall/X50YdBe5oMKqHHPNiPzEg==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "2.x",
        "rc-motion": "^2.0.1",
        "rc-overflow": "^1.0.0",
        "rc-trigger": "^5.0.4",
        "rc-util": "^5.16.1",
        "rc-virtual-list": "^3.2.0"
      },
      "engines": {
        "node": ">=8.x"
      },
      "peerDependencies": {
        "react": "*",
        "react-dom": "*"
      }
    },
    "node_modules/rc-slider": {
      "version": "10.0.1",
      "resolved": "https://registry.npmjs.org/rc-slider/-/rc-slider-10.0.1.tgz",
      "integrity": "sha512-igTKF3zBet7oS/3yNiIlmU8KnZ45npmrmHlUUio8PNbIhzMcsh+oE/r2UD42Y6YD2D/s+kzCQkzQrPD6RY435Q==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "^2.2.5",
        "rc-util": "^5.18.1",
        "shallowequal": "^1.1.0"
      },
      "engines": {
        "node": ">=8.x"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-steps": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/rc-steps/-/rc-steps-5.0.0.tgz",
      "integrity": "sha512-9TgRvnVYirdhbV0C3syJFj9EhCRqoJAsxt4i1rED5o8/ZcSv5TLIYyo4H8MCjLPvbe2R+oBAm/IYBEtC+OS1Rw==",
      "dependencies": {
        "@babel/runtime": "^7.16.7",
        "classnames": "^2.2.3",
        "rc-util": "^5.16.1"
      },
      "engines": {
        "node": ">=8.x"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-switch": {
      "version": "3.2.2",
      "resolved": "https://registry.npmjs.org/rc-switch/-/rc-switch-3.2.2.tgz",
      "integrity": "sha512-+gUJClsZZzvAHGy1vZfnwySxj+MjLlGRyXKXScrtCTcmiYNPzxDFOxdQ/3pK1Kt/0POvwJ/6ALOR8gwdXGhs+A==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "^2.2.1",
        "rc-util": "^5.0.1"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-table": {
      "version": "7.26.0",
      "resolved": "https://registry.npmjs.org/rc-table/-/rc-table-7.26.0.tgz",
      "integrity": "sha512-0cD8e6S+DTGAt5nBZQIPFYEaIukn17sfa5uFL98faHlH/whZzD8ii3dbFL4wmUDEL4BLybhYop+QUfZJ4CPvNQ==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "^2.2.5",
        "rc-resize-observer": "^1.1.0",
        "rc-util": "^5.22.5",
        "shallowequal": "^1.1.0"
      },
      "engines": {
        "node": ">=8.x"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-tabs": {
      "version": "12.5.10",
      "resolved": "https://registry.npmjs.org/rc-tabs/-/rc-tabs-12.5.10.tgz",
      "integrity": "sha512-Ay0l0jtd4eXepFH9vWBvinBjqOpqzcsJTerBGwJy435P2S90Uu38q8U/mvc1sxUEVOXX5ZCFbxcWPnfG3dH+tQ==",
      "dependencies": {
        "@babel/runtime": "^7.11.2",
        "classnames": "2.x",
        "rc-dropdown": "~4.0.0",
        "rc-menu": "~9.8.0",
        "rc-motion": "^2.6.2",
        "rc-resize-observer": "^1.0.0",
        "rc-util": "^5.16.0"
      },
      "engines": {
        "node": ">=8.x"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-textarea": {
      "version": "0.4.7",
      "resolved": "https://registry.npmjs.org/rc-textarea/-/rc-textarea-0.4.7.tgz",
      "integrity": "sha512-IQPd1CDI3mnMlkFyzt2O4gQ2lxUsnBAeJEoZGJnkkXgORNqyM9qovdrCj9NzcRfpHgLdzaEbU3AmobNFGUznwQ==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "^2.2.1",
        "rc-resize-observer": "^1.0.0",
        "rc-util": "^5.24.4",
        "shallowequal": "^1.1.0"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-tooltip": {
      "version": "5.2.2",
      "resolved": "https://registry.npmjs.org/rc-tooltip/-/rc-tooltip-5.2.2.tgz",
      "integrity": "sha512-jtQzU/18S6EI3lhSGoDYhPqNpWajMtS5VV/ld1LwyfrDByQpYmw/LW6U7oFXXLukjfDHQ7Ju705A82PRNFWYhg==",
      "dependencies": {
        "@babel/runtime": "^7.11.2",
        "classnames": "^2.3.1",
        "rc-trigger": "^5.0.0"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-tree": {
      "version": "5.7.12",
      "resolved": "https://registry.npmjs.org/rc-tree/-/rc-tree-5.7.12.tgz",
      "integrity": "sha512-LXA5nY2hG5koIAlHW5sgXgLpOMz+bFRbnZZ+cCg0tQs4Wv1AmY7EDi1SK7iFXhslYockbqUerQan82jljoaItg==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "2.x",
        "rc-motion": "^2.0.1",
        "rc-util": "^5.16.1",
        "rc-virtual-list": "^3.5.1"
      },
      "engines": {
        "node": ">=10.x"
      },
      "peerDependencies": {
        "react": "*",
        "react-dom": "*"
      }
    },
    "node_modules/rc-tree-select": {
      "version": "5.5.5",
      "resolved": "https://registry.npmjs.org/rc-tree-select/-/rc-tree-select-5.5.5.tgz",
      "integrity": "sha512-k2av7jF6tW9bIO4mQhaVdV4kJ1c54oxV3/hHVU+oD251Gb5JN+m1RbJFTMf1o0rAFqkvto33rxMdpafaGKQRJw==",
      "dependencies": {
        "@babel/runtime": "^7.10.1",
        "classnames": "2.x",
        "rc-select": "~14.1.0",
        "rc-tree": "~5.7.0",
        "rc-util": "^5.16.1"
      },
      "peerDependencies": {
        "react": "*",
        "react-dom": "*"
      }
    },
    "node_modules/rc-trigger": {
      "version": "5.3.4",
      "resolved": "https://registry.npmjs.org/rc-trigger/-/rc-trigger-5.3.4.tgz",
      "integrity": "sha512-mQv+vas0TwKcjAO2izNPkqR4j86OemLRmvL2nOzdP9OWNWA1ivoTt5hzFqYNW9zACwmTezRiN8bttrC7cZzYSw==",
      "dependencies": {
        "@babel/runtime": "^7.18.3",
        "classnames": "^2.2.6",
        "rc-align": "^4.0.0",
        "rc-motion": "^2.0.0",
        "rc-util": "^5.19.2"
      },
      "engines": {
        "node": ">=8.x"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-upload": {
      "version": "4.3.6",
      "resolved": "https://registry.npmjs.org/rc-upload/-/rc-upload-4.3.6.tgz",
      "integrity": "sha512-Bt7ESeG5tT3IY82fZcP+s0tQU2xmo1W6P3S8NboUUliquJLQYLkUcsaExi3IlBVr43GQMCjo30RA2o0i70+NjA==",
      "dependencies": {
        "@babel/runtime": "^7.18.3",
        "classnames": "^2.2.5",
        "rc-util": "^5.2.0"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-util": {
      "version": "5.43.0",
      "resolved": "https://registry.npmjs.org/rc-util/-/rc-util-5.43.0.tgz",
      "integrity": "sha512-AzC7KKOXFqAdIBqdGWepL9Xn7cm3vnAmjlHqUnoQaTMZYhM4VlXGLkkHHxj/BZ7Td0+SOPKB4RGPboBVKT9htw==",
      "dependencies": {
        "@babel/runtime": "^7.18.3",
        "react-is": "^18.2.0"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/rc-util/node_modules/react-is": {
      "version": "18.3.1",
      "resolved": "https://registry.npmjs.org/react-is/-/react-is-18.3.1.tgz",
      "integrity": "sha512-/LLMVyas0ljjAtoYiPqYiL8VWXzUUdThrmU5+n20DZv+a+ClRoevUzw5JxU+Ieh5/c87ytoTBV9G1FiKfNJdmg=="
    },
    "node_modules/rc-virtual-list": {
      "version": "3.14.8",
      "resolved": "https://registry.npmjs.org/rc-virtual-list/-/rc-virtual-list-3.14.8.tgz",
      "integrity": "sha512-8D0KfzpRYi6YZvlOWIxiOm9BGt4Wf2hQyEaM6RXlDDiY2NhLheuYI+RA+7ZaZj1lq+XQqy3KHlaeeXQfzI5fGg==",
      "dependencies": {
        "@babel/runtime": "^7.20.0",
        "classnames": "^2.2.6",
        "rc-resize-observer": "^1.0.0",
        "rc-util": "^5.36.0"
      },
      "engines": {
        "node": ">=8.x"
      },
      "peerDependencies": {
        "react": ">=16.9.0",
        "react-dom": ">=16.9.0"
      }
    },
    "node_modules/react": {
      "version": "18.3.1",
      "resolved": "https://registry.npmjs.org/react/-/react-18.3.1.tgz",
      "integrity": "sha512-wS+hAgJShR0KhEvPJArfuPVN1+Hz1t0Y6n5jLrGQbkb4urgPE/0Rve+1kMB1v/oWgHgm4WIcV+i7F2pTVj+2iQ==",
      "dependencies": {
        "loose-envify": "^1.1.0"
      },
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/react-copy-to-clipboard": {
      "version": "5.1.0",
      "resolved": "https://registry.npmjs.org/react-copy-to-clipboard/-/react-copy-to-clipboard-5.1.0.tgz",
      "integrity": "sha512-k61RsNgAayIJNoy9yDsYzDe/yAZAzEbEgcz3DZMhF686LEyukcE1hzurxe85JandPUG+yTfGVFzuEw3xt8WP/A==",
      "dependencies": {
        "copy-to-clipboard": "^3.3.1",
        "prop-types": "^15.8.1"
      },
      "peerDependencies": {
        "react": "^15.3.0 || 16 || 17 || 18"
      }
    },
    "node_modules/react-dom": {
      "version": "18.3.1",
      "resolved": "https://registry.npmjs.org/react-dom/-/react-dom-18.3.1.tgz",
      "integrity": "sha512-5m4nQKp+rZRb09LNH59GM4BxTh9251/ylbKIbpe7TpGxfJ+9kv6BLkLBXIjjspbgbnIBNqlI23tRnTWT0snUIw==",
      "dependencies": {
        "loose-envify": "^1.1.0",
        "scheduler": "^0.23.2"
      },
      "peerDependencies": {
        "react": "^18.3.1"
      }
    },
    "node_modules/react-fast-compare": {
      "version": "3.2.2",
      "resolved": "https://registry.npmjs.org/react-fast-compare/-/react-fast-compare-3.2.2.tgz",
      "integrity": "sha512-nsO+KSNgo1SbJqJEYRE9ERzo7YtYbou/OqjSQKxV7jcKox7+usiUVZOAC+XnDOABXggQTno0Y1CpVnuWEc1boQ=="
    },
    "node_modules/react-i18next": {
      "version": "12.3.1",
      "resolved": "https://registry.npmjs.org/react-i18next/-/react-i18next-12.3.1.tgz",
      "integrity": "sha512-5v8E2XjZDFzK7K87eSwC7AJcAkcLt5xYZ4+yTPDAW1i7C93oOY1dnr4BaQM7un4Hm+GmghuiPvevWwlca5PwDA==",
      "dependencies": {
        "@babel/runtime": "^7.20.6",
        "html-parse-stringify": "^3.0.1"
      },
      "peerDependencies": {
        "i18next": ">= 19.0.0",
        "react": ">= 16.8.0"
      },
      "peerDependenciesMeta": {
        "react-dom": {
          "optional": true
        },
        "react-native": {
          "optional": true
        }
      }
    },
    "node_modules/react-is": {
      "version": "16.13.1",
      "resolved": "https://registry.npmjs.org/react-is/-/react-is-16.13.1.tgz",
      "integrity": "sha512-24e6ynE2H+OKt4kqsOvNd8kBpV65zoxbA4BVsEOB3ARVWQki/DHzaUoC5KuON/BiccDaCCTZBuOcfZs70kR8bQ=="
    },
    "node_modules/react-refresh": {
      "version": "0.14.2",
      "resolved": "https://registry.npmjs.org/react-refresh/-/react-refresh-0.14.2.tgz",
      "integrity": "sha512-jCvmsr+1IUSMUyzOkRcvnVbX3ZYC6g9TDrDbFuFmRDq7PD4yaGbLKNQL6k2jnArV8hjYxh7hVhAZB6s9HDGpZA==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/react-router": {
      "version": "6.27.0",
      "resolved": "https://registry.npmjs.org/react-router/-/react-router-6.27.0.tgz",
      "integrity": "sha512-YA+HGZXz4jaAkVoYBE98VQl+nVzI+cVI2Oj/06F5ZM+0u3TgedN9Y9kmMRo2mnkSK2nCpNQn0DVob4HCsY/WLw==",
      "dependencies": {
        "@remix-run/router": "1.20.0"
      },
      "engines": {
        "node": ">=14.0.0"
      },
      "peerDependencies": {
        "react": ">=16.8"
      }
    },
    "node_modules/react-router-dom": {
      "version": "6.27.0",
      "resolved": "https://registry.npmjs.org/react-router-dom/-/react-router-dom-6.27.0.tgz",
      "integrity": "sha512-+bvtFWMC0DgAFrfKXKG9Fc+BcXWRUO1aJIihbB79xaeq0v5UzfvnM5houGUm1Y461WVRcgAQ+Clh5rdb1eCx4g==",
      "dependencies": {
        "@remix-run/router": "1.20.0",
        "react-router": "6.27.0"
      },
      "engines": {
        "node": ">=14.0.0"
      },
      "peerDependencies": {
        "react": ">=16.8",
        "react-dom": ">=16.8"
      }
    },
    "node_modules/react-shadow": {
      "version": "20.5.0",
      "resolved": "https://registry.npmjs.org/react-shadow/-/react-shadow-20.5.0.tgz",
      "integrity": "sha512-DHukRfWpJrFtZMcZrKrqU3ZwuHjTpTbrjnJdTGZQE3lqtC5ivBDVWqAVVW6lR3Lq6bhphjAbqaJU8NOoTRSCsg==",
      "dependencies": {
        "humps": "^2.0.1"
      },
      "peerDependencies": {
        "prop-types": "^15.0.0",
        "react": "^16.8.0 || ^17.0.0 || ^18.0.0",
        "react-dom": "^16.0.0 || ^17.0.0 || ^18.0.0"
      }
    },
    "node_modules/react-svg": {
      "version": "16.1.34",
      "resolved": "https://registry.npmjs.org/react-svg/-/react-svg-16.1.34.tgz",
      "integrity": "sha512-L4ak1qNFLgzVbHm0xQEpHoIOqb3um/B0ybahd3U2TKoGZxb0JaPVI5lsAhvSng2P1kcsYEok2Z7RpcKx7arJGw==",
      "dependencies": {
        "@babel/runtime": "^7.24.1",
        "@tanem/svg-injector": "^10.1.68",
        "@types/prop-types": "^15.7.12",
        "prop-types": "^15.8.1"
      },
      "peerDependencies": {
        "react": "^16.0.0 || ^17.0.0 || ^18.0.0",
        "react-dom": "^16.0.0 || ^17.0.0 || ^18.0.0"
      }
    },
    "node_modules/read-cache": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/read-cache/-/read-cache-1.0.0.tgz",
      "integrity": "sha512-Owdv/Ft7IjOgm/i0xvNDZ1LrRANRfew4b2prF3OWMQLxLfu3bS8FVhCsrSCMK4lR56Y9ya+AThoTpDCTxCmpRA==",
      "dev": true,
      "dependencies": {
        "pify": "^2.3.0"
      }
    },
    "node_modules/read-cache/node_modules/pify": {
      "version": "2.3.0",
      "resolved": "https://registry.npmjs.org/pify/-/pify-2.3.0.tgz",
      "integrity": "sha512-udgsAY+fTnvv7kI7aaxbqwWNb0AHiB0qBO89PZKPkoTmGOgdbrHDKD+0B2X4uTfJ/FT1R09r9gTsjUjNJotuog==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/readable-stream": {
      "version": "3.6.2",
      "resolved": "https://registry.npmjs.org/readable-stream/-/readable-stream-3.6.2.tgz",
      "integrity": "sha512-9u/sniCrY3D5WdsERHzHE4G2YCXqoG5FTHUiCC4SIbr6XcLZBY05ya9EKjYek9O5xOAwjGq+1JdGBAS7Q9ScoA==",
      "dependencies": {
        "inherits": "^2.0.3",
        "string_decoder": "^1.1.1",
        "util-deprecate": "^1.0.1"
      },
      "engines": {
        "node": ">= 6"
      }
    },
    "node_modules/readdirp": {
      "version": "3.6.0",
      "resolved": "https://registry.npmjs.org/readdirp/-/readdirp-3.6.0.tgz",
      "integrity": "sha512-hOS089on8RduqdbhvQ5Z37A0ESjsqz6qnRcffsMU3495FuTdqSm+7bhJ29JvIOsBDEEnan5DPu9t3To9VRlMzA==",
      "dependencies": {
        "picomatch": "^2.2.1"
      },
      "engines": {
        "node": ">=8.10.0"
      }
    },
    "node_modules/real-require": {
      "version": "0.1.0",
      "resolved": "https://registry.npmjs.org/real-require/-/real-require-0.1.0.tgz",
      "integrity": "sha512-r/H9MzAWtrv8aSVjPCMFpDMl5q66GqtmmRkRjpHTsp4zBAa+snZyiQNlMONiUmEJcsnaw0wCauJ2GWODr/aFkg==",
      "engines": {
        "node": ">= 12.13.0"
      }
    },
    "node_modules/regenerator-runtime": {
      "version": "0.14.1",
      "resolved": "https://registry.npmjs.org/regenerator-runtime/-/regenerator-runtime-0.14.1.tgz",
      "integrity": "sha512-dYnhHh0nJoMfnkZs6GmmhFknAGRrLznOu5nc9ML+EJxGvrx6H7teuevqVqCuPcPK//3eDrrjQhehXVx9cnkGdw=="
    },
    "node_modules/require-directory": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/require-directory/-/require-directory-2.1.1.tgz",
      "integrity": "sha512-fGxEI7+wsG9xrvdjsrlmL22OMTTiHRwAMroiEeMgq8gzoLC/PQr7RsRDSTLUg/bZAZtF+TVIkHc6/4RIKrui+Q==",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/require-main-filename": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/require-main-filename/-/require-main-filename-2.0.0.tgz",
      "integrity": "sha512-NKN5kMDylKuldxYLSUfrbo5Tuzh4hd+2E8NPPX02mZtn1VuREQToYe/ZdlJy+J3uCpfaiGF05e7B8W0iXbQHmg=="
    },
    "node_modules/resize-observer-polyfill": {
      "version": "1.5.1",
      "resolved": "https://registry.npmjs.org/resize-observer-polyfill/-/resize-observer-polyfill-1.5.1.tgz",
      "integrity": "sha512-LwZrotdHOo12nQuZlHEmtuXdqGoOD0OhaxopaNFxWzInpEgaLWoVuAMbTzixuosCx2nEG58ngzW3vxdWoxIgdg=="
    },
    "node_modules/resolve": {
      "version": "1.22.8",
      "resolved": "https://registry.npmjs.org/resolve/-/resolve-1.22.8.tgz",
      "integrity": "sha512-oKWePCxqpd6FlLvGV1VU0x7bkPmmCNolxzjMf4NczoDnQcIWrAF+cPtZn5i6n+RfD2d9i0tzpKnG6Yk168yIyw==",
      "dev": true,
      "dependencies": {
        "is-core-module": "^2.13.0",
        "path-parse": "^1.0.7",
        "supports-preserve-symlinks-flag": "^1.0.0"
      },
      "bin": {
        "resolve": "bin/resolve"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/resolve-from": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/resolve-from/-/resolve-from-4.0.0.tgz",
      "integrity": "sha512-pb/MYmXstAkysRFx8piNI1tGFNQIFA3vkE3Gq4EuA1dF6gHp/+vgZqsCGJapvy8N3Q+4o7FwvquPJcnZ7RYy4g==",
      "dev": true,
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/reusify": {
      "version": "1.0.4",
      "resolved": "https://registry.npmjs.org/reusify/-/reusify-1.0.4.tgz",
      "integrity": "sha512-U9nH88a3fc/ekCF1l0/UP1IosiuIjyTh7hBvXVMHYgVcfGvt897Xguj2UOLDeI5BG2m7/uwyaLVT6fbtCwTyzw==",
      "dev": true,
      "engines": {
        "iojs": ">=1.0.0",
        "node": ">=0.10.0"
      }
    },
    "node_modules/rimraf": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/rimraf/-/rimraf-3.0.2.tgz",
      "integrity": "sha512-JZkJMZkAGFFPP2YqXZXPbMlMBgsxzE8ILs4lMIX/2o0L9UBw9O/Y3o6wFw/i9YLapcUJWwqbi3kdxIPdC62TIA==",
      "deprecated": "Rimraf versions prior to v4 are no longer supported",
      "dev": true,
      "dependencies": {
        "glob": "^7.1.3"
      },
      "bin": {
        "rimraf": "bin.js"
      },
      "funding": {
        "url": "https://github.com/sponsors/isaacs"
      }
    },
    "node_modules/rollup": {
      "version": "4.24.3",
      "resolved": "https://registry.npmjs.org/rollup/-/rollup-4.24.3.tgz",
      "integrity": "sha512-HBW896xR5HGmoksbi3JBDtmVzWiPAYqp7wip50hjQ67JbDz61nyoMPdqu1DvVW9asYb2M65Z20ZHsyJCMqMyDg==",
      "dev": true,
      "dependencies": {
        "@types/estree": "1.0.6"
      },
      "bin": {
        "rollup": "dist/bin/rollup"
      },
      "engines": {
        "node": ">=18.0.0",
        "npm": ">=8.0.0"
      },
      "optionalDependencies": {
        "@rollup/rollup-android-arm-eabi": "4.24.3",
        "@rollup/rollup-android-arm64": "4.24.3",
        "@rollup/rollup-darwin-arm64": "4.24.3",
        "@rollup/rollup-darwin-x64": "4.24.3",
        "@rollup/rollup-freebsd-arm64": "4.24.3",
        "@rollup/rollup-freebsd-x64": "4.24.3",
        "@rollup/rollup-linux-arm-gnueabihf": "4.24.3",
        "@rollup/rollup-linux-arm-musleabihf": "4.24.3",
        "@rollup/rollup-linux-arm64-gnu": "4.24.3",
        "@rollup/rollup-linux-arm64-musl": "4.24.3",
        "@rollup/rollup-linux-powerpc64le-gnu": "4.24.3",
        "@rollup/rollup-linux-riscv64-gnu": "4.24.3",
        "@rollup/rollup-linux-s390x-gnu": "4.24.3",
        "@rollup/rollup-linux-x64-gnu": "4.24.3",
        "@rollup/rollup-linux-x64-musl": "4.24.3",
        "@rollup/rollup-win32-arm64-msvc": "4.24.3",
        "@rollup/rollup-win32-ia32-msvc": "4.24.3",
        "@rollup/rollup-win32-x64-msvc": "4.24.3",
        "fsevents": "~2.3.2"
      }
    },
    "node_modules/rpc-websockets": {
      "version": "9.0.4",
      "resolved": "https://registry.npmjs.org/rpc-websockets/-/rpc-websockets-9.0.4.tgz",
      "integrity": "sha512-yWZWN0M+bivtoNLnaDbtny4XchdAIF5Q4g/ZsC5UC61Ckbp0QczwO8fg44rV3uYmY4WHd+EZQbn90W1d8ojzqQ==",
      "dependencies": {
        "@swc/helpers": "^0.5.11",
        "@types/uuid": "^8.3.4",
        "@types/ws": "^8.2.2",
        "buffer": "^6.0.3",
        "eventemitter3": "^5.0.1",
        "uuid": "^8.3.2",
        "ws": "^8.5.0"
      },
      "funding": {
        "type": "paypal",
        "url": "https://paypal.me/kozjak"
      },
      "optionalDependencies": {
        "bufferutil": "^4.0.1",
        "utf-8-validate": "^5.0.2"
      }
    },
    "node_modules/rpc-websockets/node_modules/eventemitter3": {
      "version": "5.0.1",
      "resolved": "https://registry.npmjs.org/eventemitter3/-/eventemitter3-5.0.1.tgz",
      "integrity": "sha512-GWkBvjiSZK87ELrYOSESUYeVIc9mvLLf/nXalMOS5dYrgZq9o5OVkbZAVM06CVxYsCwH9BDZFPlQTlPA1j4ahA=="
    },
    "node_modules/run-parallel": {
      "version": "1.2.0",
      "resolved": "https://registry.npmjs.org/run-parallel/-/run-parallel-1.2.0.tgz",
      "integrity": "sha512-5l4VyZR86LZ/lDxZTR6jqL8AFE2S0IFLMP26AbjsLVADxHdhB/c0GUsH+y39UfCi3dzz8OlQuPmnaJOMoDHQBA==",
      "dev": true,
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/feross"
        },
        {
          "type": "patreon",
          "url": "https://www.patreon.com/feross"
        },
        {
          "type": "consulting",
          "url": "https://feross.org/support"
        }
      ],
      "dependencies": {
        "queue-microtask": "^1.2.2"
      }
    },
    "node_modules/rxjs": {
      "version": "7.8.1",
      "resolved": "https://registry.npmjs.org/rxjs/-/rxjs-7.8.1.tgz",
      "integrity": "sha512-AA3TVj+0A2iuIoQkWEK/tqFjBq2j+6PO6Y0zJcvzLAFhEFIO3HL0vls9hWLncZbAAbK0mar7oZ4V079I/qPMxg==",
      "dependencies": {
        "tslib": "^2.1.0"
      }
    },
    "node_modules/rxjs/node_modules/tslib": {
      "version": "2.8.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-2.8.1.tgz",
      "integrity": "sha512-oJFu94HQb+KVduSUQL7wnpmqnfmLsOA/nAh6b6EH0wCEoK0/mPeXU6c3wKDV83MkOuHPRHtSXKKU99IBazS/2w=="
    },
    "node_modules/safe-buffer": {
      "version": "5.2.1",
      "resolved": "https://registry.npmjs.org/safe-buffer/-/safe-buffer-5.2.1.tgz",
      "integrity": "sha512-rp3So07KcdmmKbGvgaNxQSJr7bGVSVk5S9Eq1F+ppbRo70+YeaDxkw5Dd8NPN+GD6bjnYm2VuPuCXmpuYvmCXQ==",
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/feross"
        },
        {
          "type": "patreon",
          "url": "https://www.patreon.com/feross"
        },
        {
          "type": "consulting",
          "url": "https://feross.org/support"
        }
      ]
    },
    "node_modules/safe-stable-stringify": {
      "version": "2.5.0",
      "resolved": "https://registry.npmjs.org/safe-stable-stringify/-/safe-stable-stringify-2.5.0.tgz",
      "integrity": "sha512-b3rppTKm9T+PsVCBEOUR46GWI7fdOs00VKZ1+9c1EWDaDMvjQc6tUwuFyIprgGgTcWoVHSKrU8H31ZHA2e0RHA==",
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/scheduler": {
      "version": "0.23.2",
      "resolved": "https://registry.npmjs.org/scheduler/-/scheduler-0.23.2.tgz",
      "integrity": "sha512-UOShsPwz7NrMUqhR6t0hWjFduvOzbtv7toDH1/hIrfRNIDBnnBWd0CwJTGvTpngVlmwGCdP9/Zl/tVrDqcuYzQ==",
      "dependencies": {
        "loose-envify": "^1.1.0"
      }
    },
    "node_modules/screenfull": {
      "version": "5.2.0",
      "resolved": "https://registry.npmjs.org/screenfull/-/screenfull-5.2.0.tgz",
      "integrity": "sha512-9BakfsO2aUQN2K9Fdbj87RJIEZ82Q9IGim7FqM5OsebfoFC6ZHXgDq/KvniuLTPdeM8wY2o6Dj3WQ7KeQCj3cA==",
      "engines": {
        "node": ">=0.10.0"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/scroll-into-view-if-needed": {
      "version": "2.2.31",
      "resolved": "https://registry.npmjs.org/scroll-into-view-if-needed/-/scroll-into-view-if-needed-2.2.31.tgz",
      "integrity": "sha512-dGCXy99wZQivjmjIqihaBQNjryrz5rueJY7eHfTdyWEiR4ttYpsajb14rn9s5d4DY4EcY6+4+U/maARBXJedkA==",
      "dependencies": {
        "compute-scroll-into-view": "^1.0.20"
      }
    },
    "node_modules/semver": {
      "version": "7.6.3",
      "resolved": "https://registry.npmjs.org/semver/-/semver-7.6.3.tgz",
      "integrity": "sha512-oVekP1cKtI+CTDvHWYFUcMtsK/00wmAEfyqKfNdARm8u1wNVhSgaX7A8d4UuIlUI5e84iEwOhs7ZPYRmzU9U6A==",
      "bin": {
        "semver": "bin/semver.js"
      },
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/set-blocking": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/set-blocking/-/set-blocking-2.0.0.tgz",
      "integrity": "sha512-KiKBS8AnWGEyLzofFfmvKwpdPzqiy16LvQfK3yv/fVH7Bj13/wl3JSR1J+rfgRE9q7xUJK4qvgS8raSOeLUehw=="
    },
    "node_modules/set-function-length": {
      "version": "1.2.2",
      "resolved": "https://registry.npmjs.org/set-function-length/-/set-function-length-1.2.2.tgz",
      "integrity": "sha512-pgRc4hJ4/sNjWCSS9AmnS40x3bNMDTknHgL5UaMBTMyJnU90EgWh1Rz+MC9eFu4BuN/UwZjKQuY/1v3rM7HMfg==",
      "dependencies": {
        "define-data-property": "^1.1.4",
        "es-errors": "^1.3.0",
        "function-bind": "^1.1.2",
        "get-intrinsic": "^1.2.4",
        "gopd": "^1.0.1",
        "has-property-descriptors": "^1.0.2"
      },
      "engines": {
        "node": ">= 0.4"
      }
    },
    "node_modules/sha.js": {
      "version": "2.4.11",
      "resolved": "https://registry.npmjs.org/sha.js/-/sha.js-2.4.11.tgz",
      "integrity": "sha512-QMEp5B7cftE7APOjk5Y6xgrbWu+WkLVQwk8JNjZ8nKRciZaByEW6MubieAiToS7+dwvrjGhH8jRXz3MVd0AYqQ==",
      "dependencies": {
        "inherits": "^2.0.1",
        "safe-buffer": "^5.0.1"
      },
      "bin": {
        "sha.js": "bin.js"
      }
    },
    "node_modules/shallowequal": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/shallowequal/-/shallowequal-1.1.0.tgz",
      "integrity": "sha512-y0m1JoUZSlPAjXVtPPW70aZWfIL/dSP7AFkRnniLCrK/8MDKog3TySTBmckD+RObVxH0v4Tox67+F14PdED2oQ=="
    },
    "node_modules/shebang-command": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/shebang-command/-/shebang-command-2.0.0.tgz",
      "integrity": "sha512-kHxr2zZpYtdmrN1qDjrrX/Z1rR1kG8Dx+gkpK1G4eXmvXswmcE1hTWBWYUzlraYw1/yZp6YuDY77YtvbN0dmDA==",
      "dependencies": {
        "shebang-regex": "^3.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/shebang-regex": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/shebang-regex/-/shebang-regex-3.0.0.tgz",
      "integrity": "sha512-7++dFhtcx3353uBaq8DDR4NuxBetBzC7ZQOhmTQInHEd6bSrXdiEyzCvG07Z44UYdLShWUyXt5M/yhz8ekcb1A==",
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/side-channel": {
      "version": "1.0.6",
      "resolved": "https://registry.npmjs.org/side-channel/-/side-channel-1.0.6.tgz",
      "integrity": "sha512-fDW/EZ6Q9RiO8eFG8Hj+7u/oW+XrPTIChwCOM2+th2A6OblDtYYIpve9m+KvI9Z4C9qSEXlaGR6bTEYHReuglA==",
      "dependencies": {
        "call-bind": "^1.0.7",
        "es-errors": "^1.3.0",
        "get-intrinsic": "^1.2.4",
        "object-inspect": "^1.13.1"
      },
      "engines": {
        "node": ">= 0.4"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/signal-exit": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/signal-exit/-/signal-exit-4.1.0.tgz",
      "integrity": "sha512-bzyZ1e88w9O1iNJbKnOlvYTrWPDl46O1bG0D3XInv+9tkPrxrN8jUUTiFlDkkmKWgn1M6CfIA13SuGqOa9Korw==",
      "engines": {
        "node": ">=14"
      },
      "funding": {
        "url": "https://github.com/sponsors/isaacs"
      }
    },
    "node_modules/slash": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/slash/-/slash-3.0.0.tgz",
      "integrity": "sha512-g9Q1haeby36OSStwb4ntCGGGaKsaVSjQ68fBxoQcutl5fS1vuY18H3wSt3jFyFtrkx+Kz0V1G85A4MyAdDMi2Q==",
      "dev": true,
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/sonic-boom": {
      "version": "2.8.0",
      "resolved": "https://registry.npmjs.org/sonic-boom/-/sonic-boom-2.8.0.tgz",
      "integrity": "sha512-kuonw1YOYYNOve5iHdSahXPOK49GqwA+LZhI6Wz/l0rP57iKyXXIHaRagOBHAPmGwJC6od2Z9zgvZ5loSgMlVg==",
      "dependencies": {
        "atomic-sleep": "^1.0.0"
      }
    },
    "node_modules/source-map-js": {
      "version": "1.2.1",
      "resolved": "https://registry.npmjs.org/source-map-js/-/source-map-js-1.2.1.tgz",
      "integrity": "sha512-UXWMKhLOwVKb728IUtQPXxfYU+usdybtUrK/8uGE8CQMvrhOpwvzDBwj0QhSL7MQc7vIsISBG8VQ8+IDQxpfQA==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/split": {
      "version": "0.3.3",
      "resolved": "https://registry.npmjs.org/split/-/split-0.3.3.tgz",
      "integrity": "sha512-wD2AeVmxXRBoX44wAycgjVpMhvbwdI2aZjCkvfNcH1YqHQvJVa1duWc73OyVGJUc05fhFaTZeQ/PYsrmyH0JVA==",
      "dependencies": {
        "through": "2"
      },
      "engines": {
        "node": "*"
      }
    },
    "node_modules/split-on-first": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/split-on-first/-/split-on-first-1.1.0.tgz",
      "integrity": "sha512-43ZssAJaMusuKWL8sKUBQXHWOpq8d6CfN/u1p4gUzfJkM05C8rxTmYrkIPTXapZpORA6LkkzcUulJ8FqA7Uudw==",
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/split2": {
      "version": "4.2.0",
      "resolved": "https://registry.npmjs.org/split2/-/split2-4.2.0.tgz",
      "integrity": "sha512-UcjcJOWknrNkF6PLX83qcHM6KHgVKNkV62Y8a5uYDVv9ydGQVwAHMKqHdJje1VTWpljG0WYpCDhrCdAOYH4TWg==",
      "engines": {
        "node": ">= 10.x"
      }
    },
    "node_modules/start-server-and-test": {
      "version": "1.15.4",
      "resolved": "https://registry.npmjs.org/start-server-and-test/-/start-server-and-test-1.15.4.tgz",
      "integrity": "sha512-ucQtp5+UCr0m4aHlY+aEV2JSYNTiMZKdSKK/bsIr6AlmwAWDYDnV7uGlWWEtWa7T4XvRI5cPYcPcQgeLqpz+Tg==",
      "dependencies": {
        "arg": "^5.0.2",
        "bluebird": "3.7.2",
        "check-more-types": "2.24.0",
        "debug": "4.3.4",
        "execa": "5.1.1",
        "lazy-ass": "1.6.0",
        "ps-tree": "1.2.0",
        "wait-on": "7.0.1"
      },
      "bin": {
        "server-test": "src/bin/start.js",
        "start-server-and-test": "src/bin/start.js",
        "start-test": "src/bin/start.js"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/start-server-and-test/node_modules/debug": {
      "version": "4.3.4",
      "resolved": "https://registry.npmjs.org/debug/-/debug-4.3.4.tgz",
      "integrity": "sha512-PRWFHuSU3eDtQJPvnNY7Jcket1j0t5OuOsFzPPzsekD52Zl8qUfFIPEiswXqIvHWGVHOgX+7G/vCNNhehwxfkQ==",
      "dependencies": {
        "ms": "2.1.2"
      },
      "engines": {
        "node": ">=6.0"
      },
      "peerDependenciesMeta": {
        "supports-color": {
          "optional": true
        }
      }
    },
    "node_modules/start-server-and-test/node_modules/execa": {
      "version": "5.1.1",
      "resolved": "https://registry.npmjs.org/execa/-/execa-5.1.1.tgz",
      "integrity": "sha512-8uSpZZocAZRBAPIEINJj3Lo9HyGitllczc27Eh5YYojjMFMn8yHMDMaUHE2Jqfq05D/wucwI4JGURyXt1vchyg==",
      "dependencies": {
        "cross-spawn": "^7.0.3",
        "get-stream": "^6.0.0",
        "human-signals": "^2.1.0",
        "is-stream": "^2.0.0",
        "merge-stream": "^2.0.0",
        "npm-run-path": "^4.0.1",
        "onetime": "^5.1.2",
        "signal-exit": "^3.0.3",
        "strip-final-newline": "^2.0.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sindresorhus/execa?sponsor=1"
      }
    },
    "node_modules/start-server-and-test/node_modules/get-stream": {
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/get-stream/-/get-stream-6.0.1.tgz",
      "integrity": "sha512-ts6Wi+2j3jQjqi70w5AlN8DFnkSwC+MqmxEzdEALB2qXZYV3X/b1CTfgPLGJNMeAWxdPfU8FO1ms3NUfaHCPYg==",
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/start-server-and-test/node_modules/human-signals": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/human-signals/-/human-signals-2.1.0.tgz",
      "integrity": "sha512-B4FFZ6q/T2jhhksgkbEW3HBvWIfDW85snkQgawt07S7J5QXTk6BkNV+0yAeZrM5QpMAdYlocGoljn0sJ/WQkFw==",
      "engines": {
        "node": ">=10.17.0"
      }
    },
    "node_modules/start-server-and-test/node_modules/is-stream": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/is-stream/-/is-stream-2.0.1.tgz",
      "integrity": "sha512-hFoiJiTl63nn+kstHGBtewWSKnQLpyb155KHheA1l39uvtO9nWIop1p3udqPcUd/xbF1VLMO4n7OI6p7RbngDg==",
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/start-server-and-test/node_modules/mimic-fn": {
      "version": "2.1.0",
      "resolved": "https://registry.npmjs.org/mimic-fn/-/mimic-fn-2.1.0.tgz",
      "integrity": "sha512-OqbOk5oEQeAZ8WXWydlu9HJjz9WVdEIvamMCcXmuqUYjTknH/sqsWvhQ3vgwKFRR1HpjvNBKQ37nbJgYzGqGcg==",
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/start-server-and-test/node_modules/ms": {
      "version": "2.1.2",
      "resolved": "https://registry.npmjs.org/ms/-/ms-2.1.2.tgz",
      "integrity": "sha512-sGkPx+VjMtmA6MX27oA4FBFELFCZZ4S4XqeGOXCv68tT+jb3vk/RyaKWP0PTKyWtmLSM0b+adUTEvbs1PEaH2w=="
    },
    "node_modules/start-server-and-test/node_modules/npm-run-path": {
      "version": "4.0.1",
      "resolved": "https://registry.npmjs.org/npm-run-path/-/npm-run-path-4.0.1.tgz",
      "integrity": "sha512-S48WzZW777zhNIrn7gxOlISNAqi9ZC/uQFnRdbeIHhZhCA6UqpkOT8T1G7BvfdgP4Er8gF4sUbaS0i7QvIfCWw==",
      "dependencies": {
        "path-key": "^3.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/start-server-and-test/node_modules/onetime": {
      "version": "5.1.2",
      "resolved": "https://registry.npmjs.org/onetime/-/onetime-5.1.2.tgz",
      "integrity": "sha512-kbpaSSGJTWdAY5KPVeMOKXSrPtr8C8C7wodJbcsd51jRnmD+GZu8Y0VoU6Dm5Z4vWr0Ig/1NKuWRKf7j5aaYSg==",
      "dependencies": {
        "mimic-fn": "^2.1.0"
      },
      "engines": {
        "node": ">=6"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/start-server-and-test/node_modules/signal-exit": {
      "version": "3.0.7",
      "resolved": "https://registry.npmjs.org/signal-exit/-/signal-exit-3.0.7.tgz",
      "integrity": "sha512-wnD2ZE+l+SPC/uoS0vXeE9L1+0wuaMqKlfz9AMUo38JsyLSBWSFcHR1Rri62LZc12vLr1gb3jl7iwQhgwpAbGQ=="
    },
    "node_modules/start-server-and-test/node_modules/strip-final-newline": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/strip-final-newline/-/strip-final-newline-2.0.0.tgz",
      "integrity": "sha512-BrpvfNAE3dcvq7ll3xVumzjKjZQ5tI1sEUIKr3Uoks0XUl45St3FlatVqef9prk4jRDzhW6WZg+3bk93y6pLjA==",
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/std-env": {
      "version": "3.7.0",
      "resolved": "https://registry.npmjs.org/std-env/-/std-env-3.7.0.tgz",
      "integrity": "sha512-JPbdCEQLj1w5GilpiHAx3qJvFndqybBysA3qUOnznweH4QbNYUsW/ea8QzSrnh0vNsezMMw5bcVool8lM0gwzg=="
    },
    "node_modules/stream-combiner": {
      "version": "0.0.4",
      "resolved": "https://registry.npmjs.org/stream-combiner/-/stream-combiner-0.0.4.tgz",
      "integrity": "sha512-rT00SPnTVyRsaSz5zgSPma/aHSOic5U1prhYdRy5HS2kTZviFpmDgzilbtsJsxiroqACmayynDN/9VzIbX5DOw==",
      "dependencies": {
        "duplexer": "~0.1.1"
      }
    },
    "node_modules/stream-shift": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/stream-shift/-/stream-shift-1.0.3.tgz",
      "integrity": "sha512-76ORR0DO1o1hlKwTbi/DM3EXWGf3ZJYO8cXX5RJwnul2DEg2oyoZyjLNoQM8WsvZiFKCRfC1O0J7iCvie3RZmQ=="
    },
    "node_modules/strict-uri-encode": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/strict-uri-encode/-/strict-uri-encode-2.0.0.tgz",
      "integrity": "sha512-QwiXZgpRcKkhTj2Scnn++4PKtWsH0kpzZ62L2R6c/LUVYv7hVnZqcg2+sMuT6R7Jusu1vviK/MFsu6kNJfWlEQ==",
      "engines": {
        "node": ">=4"
      }
    },
    "node_modules/string_decoder": {
      "version": "1.3.0",
      "resolved": "https://registry.npmjs.org/string_decoder/-/string_decoder-1.3.0.tgz",
      "integrity": "sha512-hkRX8U1WjJFd8LsDJ2yQ/wWWxaopEsABU1XfkM8A+j0+85JAGppt16cr1Whg6KIbb4okU6Mql6BOj+uup/wKeA==",
      "dependencies": {
        "safe-buffer": "~5.2.0"
      }
    },
    "node_modules/string-convert": {
      "version": "0.2.1",
      "resolved": "https://registry.npmjs.org/string-convert/-/string-convert-0.2.1.tgz",
      "integrity": "sha512-u/1tdPl4yQnPBjnVrmdLo9gtuLvELKsAoRapekWggdiQNvvvum+jYF329d84NAa660KQw7pB2n36KrIKVoXa3A=="
    },
    "node_modules/string-width": {
      "version": "4.2.3",
      "resolved": "https://registry.npmjs.org/string-width/-/string-width-4.2.3.tgz",
      "integrity": "sha512-wKyQRQpjJ0sIp62ErSZdGsjMJWsap5oRNihHhu6G7JVO/9jIB6UyevL+tXuOqrng8j/cxKTWyWUwvSTriiZz/g==",
      "dependencies": {
        "emoji-regex": "^8.0.0",
        "is-fullwidth-code-point": "^3.0.0",
        "strip-ansi": "^6.0.1"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/string-width-cjs": {
      "name": "string-width",
      "version": "4.2.3",
      "resolved": "https://registry.npmjs.org/string-width/-/string-width-4.2.3.tgz",
      "integrity": "sha512-wKyQRQpjJ0sIp62ErSZdGsjMJWsap5oRNihHhu6G7JVO/9jIB6UyevL+tXuOqrng8j/cxKTWyWUwvSTriiZz/g==",
      "dev": true,
      "dependencies": {
        "emoji-regex": "^8.0.0",
        "is-fullwidth-code-point": "^3.0.0",
        "strip-ansi": "^6.0.1"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/strip-ansi": {
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/strip-ansi/-/strip-ansi-6.0.1.tgz",
      "integrity": "sha512-Y38VPSHcqkFrCpFnQ9vuSXmquuv5oXOKpGeT6aGrr3o3Gc9AlVa6JBfUSOCnbxGGZF+/0ooI7KrPuUSztUdU5A==",
      "dependencies": {
        "ansi-regex": "^5.0.1"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/strip-ansi-cjs": {
      "name": "strip-ansi",
      "version": "6.0.1",
      "resolved": "https://registry.npmjs.org/strip-ansi/-/strip-ansi-6.0.1.tgz",
      "integrity": "sha512-Y38VPSHcqkFrCpFnQ9vuSXmquuv5oXOKpGeT6aGrr3o3Gc9AlVa6JBfUSOCnbxGGZF+/0ooI7KrPuUSztUdU5A==",
      "dev": true,
      "dependencies": {
        "ansi-regex": "^5.0.1"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/strip-eof": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/strip-eof/-/strip-eof-1.0.0.tgz",
      "integrity": "sha512-7FCwGGmx8mD5xQd3RPUvnSpUXHM3BWuzjtpD4TXsfcZ9EL4azvVVUscFYwD9nx8Kh+uCBC00XBtAykoMHwTh8Q==",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/strip-final-newline": {
      "version": "3.0.0",
      "resolved": "https://registry.npmjs.org/strip-final-newline/-/strip-final-newline-3.0.0.tgz",
      "integrity": "sha512-dOESqjYr96iWYylGObzd39EuNTa5VJxyvVAEm5Jnh7KGo75V43Hk1odPQkNDyXNmUR6k+gEiDVXnjB8HJ3crXw==",
      "engines": {
        "node": ">=12"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/strip-hex-prefix": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/strip-hex-prefix/-/strip-hex-prefix-1.0.0.tgz",
      "integrity": "sha512-q8d4ue7JGEiVcypji1bALTos+0pWtyGlivAWyPuTkHzuTCJqrK9sWxYQZUq6Nq3cuyv3bm734IhHvHtGGURU6A==",
      "dependencies": {
        "is-hex-prefixed": "1.0.0"
      },
      "engines": {
        "node": ">=6.5.0",
        "npm": ">=3"
      }
    },
    "node_modules/strip-json-comments": {
      "version": "3.1.1",
      "resolved": "https://registry.npmjs.org/strip-json-comments/-/strip-json-comments-3.1.1.tgz",
      "integrity": "sha512-6fPc+R4ihwqP6N/aIv2f1gMH8lOVtWQHoqC4yK6oSDVVocumAsfCqjkXnqiYMhmMwS/mEHLp7Vehlt3ql6lEig==",
      "dev": true,
      "engines": {
        "node": ">=8"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/strnum": {
      "version": "1.0.5",
      "resolved": "https://registry.npmjs.org/strnum/-/strnum-1.0.5.tgz",
      "integrity": "sha512-J8bbNyKKXl5qYcR36TIO8W3mVGVHrmmxsd5PAItGkmyzwJvybiw2IVq5nqd0i4LSNSkB/sx9VHllbfFdr9k1JA=="
    },
    "node_modules/sucrase": {
      "version": "3.35.0",
      "resolved": "https://registry.npmjs.org/sucrase/-/sucrase-3.35.0.tgz",
      "integrity": "sha512-8EbVDiu9iN/nESwxeSxDKe0dunta1GOlHufmSSXxMD2z2/tMZpDMpvXQGsc+ajGo8y2uYUmixaSRUc/QPoQ0GA==",
      "dev": true,
      "dependencies": {
        "@jridgewell/gen-mapping": "^0.3.2",
        "commander": "^4.0.0",
        "glob": "^10.3.10",
        "lines-and-columns": "^1.1.6",
        "mz": "^2.7.0",
        "pirates": "^4.0.1",
        "ts-interface-checker": "^0.1.9"
      },
      "bin": {
        "sucrase": "bin/sucrase",
        "sucrase-node": "bin/sucrase-node"
      },
      "engines": {
        "node": ">=16 || 14 >=14.17"
      }
    },
    "node_modules/sucrase/node_modules/commander": {
      "version": "4.1.1",
      "resolved": "https://registry.npmjs.org/commander/-/commander-4.1.1.tgz",
      "integrity": "sha512-NOKm8xhkzAjzFx8B2v5OAHT+u5pRQc2UCa2Vq9jYL/31o2wi9mxBA7LIFs3sV5VSC49z6pEhfbMULvShKj26WA==",
      "dev": true,
      "engines": {
        "node": ">= 6"
      }
    },
    "node_modules/sucrase/node_modules/glob": {
      "version": "10.4.5",
      "resolved": "https://registry.npmjs.org/glob/-/glob-10.4.5.tgz",
      "integrity": "sha512-7Bv8RF0k6xjo7d4A/PxYLbUCfb6c+Vpd2/mB2yRDlew7Jb5hEXiCD9ibfO7wpk8i4sevK6DFny9h7EYbM3/sHg==",
      "dev": true,
      "dependencies": {
        "foreground-child": "^3.1.0",
        "jackspeak": "^3.1.2",
        "minimatch": "^9.0.4",
        "minipass": "^7.1.2",
        "package-json-from-dist": "^1.0.0",
        "path-scurry": "^1.11.1"
      },
      "bin": {
        "glob": "dist/esm/bin.mjs"
      },
      "funding": {
        "url": "https://github.com/sponsors/isaacs"
      }
    },
    "node_modules/sucrase/node_modules/minimatch": {
      "version": "9.0.5",
      "resolved": "https://registry.npmjs.org/minimatch/-/minimatch-9.0.5.tgz",
      "integrity": "sha512-G6T0ZX48xgozx7587koeX9Ys2NYy6Gmv//P89sEte9V9whIapMNF4idKxnW2QtCcLiTWlb/wfCabAtAFWhhBow==",
      "dev": true,
      "dependencies": {
        "brace-expansion": "^2.0.1"
      },
      "engines": {
        "node": ">=16 || 14 >=14.17"
      },
      "funding": {
        "url": "https://github.com/sponsors/isaacs"
      }
    },
    "node_modules/superstruct": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/superstruct/-/superstruct-2.0.2.tgz",
      "integrity": "sha512-uV+TFRZdXsqXTL2pRvujROjdZQ4RAlBUS5BTh9IGm+jTqQntYThciG/qu57Gs69yjnVUSqdxF9YLmSnpupBW9A==",
      "engines": {
        "node": ">=14.0.0"
      }
    },
    "node_modules/supports-color": {
      "version": "7.2.0",
      "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-7.2.0.tgz",
      "integrity": "sha512-qpCAvRl9stuOHveKsn7HncJRvv501qIacKzQlO/+Lwxc9+0q2wLyv4Dfvt80/DPn2pqOBsJdDiogXGR9+OvwRw==",
      "dev": true,
      "dependencies": {
        "has-flag": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/supports-preserve-symlinks-flag": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/supports-preserve-symlinks-flag/-/supports-preserve-symlinks-flag-1.0.0.tgz",
      "integrity": "sha512-ot0WnXS9fgdkgIcePe6RHNk1WA8+muPa6cSjeR3V8K27q9BB1rTE3R1p7Hv0z1ZyAc8s6Vvv8DIyWf681MAt0w==",
      "dev": true,
      "engines": {
        "node": ">= 0.4"
      },
      "funding": {
        "url": "https://github.com/sponsors/ljharb"
      }
    },
    "node_modules/system-architecture": {
      "version": "0.1.0",
      "resolved": "https://registry.npmjs.org/system-architecture/-/system-architecture-0.1.0.tgz",
      "integrity": "sha512-ulAk51I9UVUyJgxlv9M6lFot2WP3e7t8Kz9+IS6D4rVba1tR9kON+Ey69f+1R4Q8cd45Lod6a4IcJIxnzGc/zA==",
      "engines": {
        "node": ">=18"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/tailwindcss": {
      "version": "3.4.14",
      "resolved": "https://registry.npmjs.org/tailwindcss/-/tailwindcss-3.4.14.tgz",
      "integrity": "sha512-IcSvOcTRcUtQQ7ILQL5quRDg7Xs93PdJEk1ZLbhhvJc7uj/OAhYOnruEiwnGgBvUtaUAJ8/mhSw1o8L2jCiENA==",
      "dev": true,
      "dependencies": {
        "@alloc/quick-lru": "^5.2.0",
        "arg": "^5.0.2",
        "chokidar": "^3.5.3",
        "didyoumean": "^1.2.2",
        "dlv": "^1.1.3",
        "fast-glob": "^3.3.0",
        "glob-parent": "^6.0.2",
        "is-glob": "^4.0.3",
        "jiti": "^1.21.0",
        "lilconfig": "^2.1.0",
        "micromatch": "^4.0.5",
        "normalize-path": "^3.0.0",
        "object-hash": "^3.0.0",
        "picocolors": "^1.0.0",
        "postcss": "^8.4.23",
        "postcss-import": "^15.1.0",
        "postcss-js": "^4.0.1",
        "postcss-load-config": "^4.0.1",
        "postcss-nested": "^6.0.1",
        "postcss-selector-parser": "^6.0.11",
        "resolve": "^1.22.2",
        "sucrase": "^3.32.0"
      },
      "bin": {
        "tailwind": "lib/cli.js",
        "tailwindcss": "lib/cli.js"
      },
      "engines": {
        "node": ">=14.0.0"
      }
    },
    "node_modules/text-encoding-utf-8": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/text-encoding-utf-8/-/text-encoding-utf-8-1.0.2.tgz",
      "integrity": "sha512-8bw4MY9WjdsD2aMtO0OzOCY3pXGYNx2d2FfHRVUKkiCPDWjKuOlhLVASS+pD7VkLTVjW268LYJHwsnPFlBpbAg=="
    },
    "node_modules/text-table": {
      "version": "0.2.0",
      "resolved": "https://registry.npmjs.org/text-table/-/text-table-0.2.0.tgz",
      "integrity": "sha512-N+8UisAXDGk8PFXP4HAzVR9nbfmVJ3zYLAWiTIoqC5v5isinhr+r5uaO8+7r3BMfuNIufIsA7RdpVgacC2cSpw==",
      "dev": true
    },
    "node_modules/thenify": {
      "version": "3.3.1",
      "resolved": "https://registry.npmjs.org/thenify/-/thenify-3.3.1.tgz",
      "integrity": "sha512-RVZSIV5IG10Hk3enotrhvz0T9em6cyHBLkH/YAZuKqd8hRkKhSfCGIcP2KUY0EPxndzANBmNllzWPwak+bheSw==",
      "dev": true,
      "dependencies": {
        "any-promise": "^1.0.0"
      }
    },
    "node_modules/thenify-all": {
      "version": "1.6.0",
      "resolved": "https://registry.npmjs.org/thenify-all/-/thenify-all-1.6.0.tgz",
      "integrity": "sha512-RNxQH/qI8/t3thXJDwcstUO4zeqo64+Uy/+sNVRBx4Xn2OX+OZ9oP+iJnNFqplFra2ZUVeKCSa2oVWi3T4uVmA==",
      "dev": true,
      "dependencies": {
        "thenify": ">= 3.1.0 < 4"
      },
      "engines": {
        "node": ">=0.8"
      }
    },
    "node_modules/thread-stream": {
      "version": "0.15.2",
      "resolved": "https://registry.npmjs.org/thread-stream/-/thread-stream-0.15.2.tgz",
      "integrity": "sha512-UkEhKIg2pD+fjkHQKyJO3yoIvAP3N6RlNFt2dUhcS1FGvCD1cQa1M/PGknCLFIyZdtJOWQjejp7bdNqmN7zwdA==",
      "dependencies": {
        "real-require": "^0.1.0"
      }
    },
    "node_modules/throttle-debounce": {
      "version": "5.0.2",
      "resolved": "https://registry.npmjs.org/throttle-debounce/-/throttle-debounce-5.0.2.tgz",
      "integrity": "sha512-B71/4oyj61iNH0KeCamLuE2rmKuTO5byTOSVwECM5FA7TiAiAW+UqTKZ9ERueC4qvgSttUhdmq1mXC3kJqGX7A==",
      "engines": {
        "node": ">=12.22"
      }
    },
    "node_modules/through": {
      "version": "2.3.8",
      "resolved": "https://registry.npmjs.org/through/-/through-2.3.8.tgz",
      "integrity": "sha512-w89qg7PI8wAdvX60bMDP+bFoD5Dvhm9oLheFp5O4a2QF0cSBGsBX4qZmadPMvVqlLJBBci+WqGGOAPvcDeNSVg=="
    },
    "node_modules/to-regex-range": {
      "version": "5.0.1",
      "resolved": "https://registry.npmjs.org/to-regex-range/-/to-regex-range-5.0.1.tgz",
      "integrity": "sha512-65P7iz6X5yEr1cwcgvQxbbIw7Uk3gOy5dIdtZ4rDveLqhrdJP+Li/Hx6tyK0NEb+2GCyneCMJiGqrADCSNk8sQ==",
      "dependencies": {
        "is-number": "^7.0.0"
      },
      "engines": {
        "node": ">=8.0"
      }
    },
    "node_modules/toggle-selection": {
      "version": "1.0.6",
      "resolved": "https://registry.npmjs.org/toggle-selection/-/toggle-selection-1.0.6.tgz",
      "integrity": "sha512-BiZS+C1OS8g/q2RRbJmy59xpyghNBqrr6k5L/uKBGRsTfxmu3ffiRnd8mlGPUVayg8pvfi5urfnu8TU7DVOkLQ=="
    },
    "node_modules/tr46": {
      "version": "0.0.3",
      "resolved": "https://registry.npmjs.org/tr46/-/tr46-0.0.3.tgz",
      "integrity": "sha512-N3WMsuqV66lT30CrXNbEjx4GEwlow3v6rr4mCcv6prnfwhS01rkgyFdjPNBYd9br7LpXV1+Emh01fHnq2Gdgrw=="
    },
    "node_modules/ts-api-utils": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/ts-api-utils/-/ts-api-utils-1.4.0.tgz",
      "integrity": "sha512-032cPxaEKwM+GT3vA5JXNzIaizx388rhsSW79vGRNGXfRRAdEAn2mvk36PvK5HnOchyWZ7afLEXqYCvPCrzuzQ==",
      "dev": true,
      "engines": {
        "node": ">=16"
      },
      "peerDependencies": {
        "typescript": ">=4.2.0"
      }
    },
    "node_modules/ts-interface-checker": {
      "version": "0.1.13",
      "resolved": "https://registry.npmjs.org/ts-interface-checker/-/ts-interface-checker-0.1.13.tgz",
      "integrity": "sha512-Y/arvbn+rrz3JCKl9C4kVNfTfSm2/mEp5FSz5EsZSANGPSlQrpRI5M4PKF+mJnE52jOO90PnPSc3Ur3bTQw0gA==",
      "dev": true
    },
    "node_modules/tslib": {
      "version": "1.14.1",
      "resolved": "https://registry.npmjs.org/tslib/-/tslib-1.14.1.tgz",
      "integrity": "sha512-Xni35NKzjgMrwevysHTCArtLDpPvye8zV/0E4EyYn43P7/7qvQwPh9BGkHewbMulVntbigmcT7rdX3BNo9wRJg=="
    },
    "node_modules/tweetnacl": {
      "version": "1.0.3",
      "resolved": "https://registry.npmjs.org/tweetnacl/-/tweetnacl-1.0.3.tgz",
      "integrity": "sha512-6rt+RN7aOi1nGMyC4Xa5DdYiukl2UWCbcJft7YhxReBGQD7OAM8Pbxw6YMo4r2diNEA8FEmu32YOn9rhaiE5yw=="
    },
    "node_modules/type-check": {
      "version": "0.4.0",
      "resolved": "https://registry.npmjs.org/type-check/-/type-check-0.4.0.tgz",
      "integrity": "sha512-XleUoc9uwGXqjWwXaUTZAmzMcFZ5858QA2vvx1Ur5xIcixXIP+8LnFDgRplU30us6teqdlskFfu+ae4K79Ooew==",
      "dev": true,
      "dependencies": {
        "prelude-ls": "^1.2.1"
      },
      "engines": {
        "node": ">= 0.8.0"
      }
    },
    "node_modules/type-fest": {
      "version": "0.20.2",
      "resolved": "https://registry.npmjs.org/type-fest/-/type-fest-0.20.2.tgz",
      "integrity": "sha512-Ne+eE4r0/iWnpAxD852z3A+N0Bt5RN//NjJwRd2VFHEmrywxf5vsZlh4R6lixl6B+wz/8d+maTSAkN1FIkI3LQ==",
      "dev": true,
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/typescript": {
      "version": "5.6.3",
      "resolved": "https://registry.npmjs.org/typescript/-/typescript-5.6.3.tgz",
      "integrity": "sha512-hjcS1mhfuyi4WW8IWtjP7brDrG2cuDZukyrYrSauoXGNgx0S7zceP07adYkJycEr56BOUTNPzbInooiN3fn1qw==",
      "devOptional": true,
      "bin": {
        "tsc": "bin/tsc",
        "tsserver": "bin/tsserver"
      },
      "engines": {
        "node": ">=14.17"
      }
    },
    "node_modules/ufo": {
      "version": "1.5.4",
      "resolved": "https://registry.npmjs.org/ufo/-/ufo-1.5.4.tgz",
      "integrity": "sha512-UsUk3byDzKd04EyoZ7U4DOlxQaD14JUKQl6/P7wiX4FNvUfm3XL246n9W5AmqwW5RSFJ27NAuM0iLscAOYUiGQ=="
    },
    "node_modules/uint8arrays": {
      "version": "3.1.1",
      "resolved": "https://registry.npmjs.org/uint8arrays/-/uint8arrays-3.1.1.tgz",
      "integrity": "sha512-+QJa8QRnbdXVpHYjLoTpJIdCTiw9Ir62nocClWuXIq2JIh4Uta0cQsTSpFL678p2CN8B+XSApwcU+pQEqVpKWg==",
      "dependencies": {
        "multiformats": "^9.4.2"
      }
    },
    "node_modules/uncrypto": {
      "version": "0.1.3",
      "resolved": "https://registry.npmjs.org/uncrypto/-/uncrypto-0.1.3.tgz",
      "integrity": "sha512-Ql87qFHB3s/De2ClA9e0gsnS6zXG27SkTiSJwjCc9MebbfapQfuPzumMIUMi38ezPZVNFcHI9sUIepeQfw8J8Q=="
    },
    "node_modules/undici-types": {
      "version": "6.19.8",
      "resolved": "https://registry.npmjs.org/undici-types/-/undici-types-6.19.8.tgz",
      "integrity": "sha512-ve2KP6f/JnbPBFyobGHuerC9g1FYGn/F8n1LWTwNxCEzd6IfqTwUQcNXgEtmmQ6DlRrC1hrSrBnCZPokRrDHjw=="
    },
    "node_modules/unenv": {
      "version": "1.10.0",
      "resolved": "https://registry.npmjs.org/unenv/-/unenv-1.10.0.tgz",
      "integrity": "sha512-wY5bskBQFL9n3Eca5XnhH6KbUo/tfvkwm9OpcdCvLaeA7piBNbavbOKJySEwQ1V0RH6HvNlSAFRTpvTqgKRQXQ==",
      "dependencies": {
        "consola": "^3.2.3",
        "defu": "^6.1.4",
        "mime": "^3.0.0",
        "node-fetch-native": "^1.6.4",
        "pathe": "^1.1.2"
      }
    },
    "node_modules/unidragger": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/unidragger/-/unidragger-3.0.1.tgz",
      "integrity": "sha512-RngbGSwBFmqGBWjkaH+yB677uzR95blSQyxq6hYbrQCejH3Mx1nm8DVOuh3M9k2fQyTstWUG5qlgCnNqV/9jVw==",
      "dependencies": {
        "ev-emitter": "^2.0.0"
      }
    },
    "node_modules/unstorage": {
      "version": "1.13.1",
      "resolved": "https://registry.npmjs.org/unstorage/-/unstorage-1.13.1.tgz",
      "integrity": "sha512-ELexQHUrG05QVIM/iUeQNdl9FXDZhqLJ4yP59fnmn2jGUh0TEulwOgov1ubOb3Gt2ZGK/VMchJwPDNVEGWQpRg==",
      "dependencies": {
        "anymatch": "^3.1.3",
        "chokidar": "^3.6.0",
        "citty": "^0.1.6",
        "destr": "^2.0.3",
        "h3": "^1.13.0",
        "listhen": "^1.9.0",
        "lru-cache": "^10.4.3",
        "node-fetch-native": "^1.6.4",
        "ofetch": "^1.4.1",
        "ufo": "^1.5.4"
      },
      "peerDependencies": {
        "@azure/app-configuration": "^1.7.0",
        "@azure/cosmos": "^4.1.1",
        "@azure/data-tables": "^13.2.2",
        "@azure/identity": "^4.5.0",
        "@azure/keyvault-secrets": "^4.9.0",
        "@azure/storage-blob": "^12.25.0",
        "@capacitor/preferences": "^6.0.2",
        "@netlify/blobs": "^6.5.0 || ^7.0.0 || ^8.1.0",
        "@planetscale/database": "^1.19.0",
        "@upstash/redis": "^1.34.3",
        "@vercel/kv": "^1.0.1",
        "idb-keyval": "^6.2.1",
        "ioredis": "^5.4.1"
      },
      "peerDependenciesMeta": {
        "@azure/app-configuration": {
          "optional": true
        },
        "@azure/cosmos": {
          "optional": true
        },
        "@azure/data-tables": {
          "optional": true
        },
        "@azure/identity": {
          "optional": true
        },
        "@azure/keyvault-secrets": {
          "optional": true
        },
        "@azure/storage-blob": {
          "optional": true
        },
        "@capacitor/preferences": {
          "optional": true
        },
        "@netlify/blobs": {
          "optional": true
        },
        "@planetscale/database": {
          "optional": true
        },
        "@upstash/redis": {
          "optional": true
        },
        "@vercel/kv": {
          "optional": true
        },
        "idb-keyval": {
          "optional": true
        },
        "ioredis": {
          "optional": true
        }
      }
    },
    "node_modules/unstorage/node_modules/lru-cache": {
      "version": "10.4.3",
      "resolved": "https://registry.npmjs.org/lru-cache/-/lru-cache-10.4.3.tgz",
      "integrity": "sha512-JNAzZcXrCt42VGLuYz0zfAzDfAvJWW6AfYlDBQyDV5DClI2m5sAmK+OIO7s59XfsRsWHp02jAJrRadPRGTt6SQ=="
    },
    "node_modules/untun": {
      "version": "0.1.3",
      "resolved": "https://registry.npmjs.org/untun/-/untun-0.1.3.tgz",
      "integrity": "sha512-4luGP9LMYszMRZwsvyUd9MrxgEGZdZuZgpVQHEEX0lCYFESasVRvZd0EYpCkOIbJKHMuv0LskpXc/8Un+MJzEQ==",
      "dependencies": {
        "citty": "^0.1.5",
        "consola": "^3.2.3",
        "pathe": "^1.1.1"
      },
      "bin": {
        "untun": "bin/untun.mjs"
      }
    },
    "node_modules/update-browserslist-db": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/update-browserslist-db/-/update-browserslist-db-1.1.1.tgz",
      "integrity": "sha512-R8UzCaa9Az+38REPiJ1tXlImTJXlVfgHZsglwBD/k6nj76ctsH1E3q4doGrukiLQd3sGQYu56r5+lo5r94l29A==",
      "dev": true,
      "funding": [
        {
          "type": "opencollective",
          "url": "https://opencollective.com/browserslist"
        },
        {
          "type": "tidelift",
          "url": "https://tidelift.com/funding/github/npm/browserslist"
        },
        {
          "type": "github",
          "url": "https://github.com/sponsors/ai"
        }
      ],
      "dependencies": {
        "escalade": "^3.2.0",
        "picocolors": "^1.1.0"
      },
      "bin": {
        "update-browserslist-db": "cli.js"
      },
      "peerDependencies": {
        "browserslist": ">= 4.21.0"
      }
    },
    "node_modules/uqr": {
      "version": "0.1.2",
      "resolved": "https://registry.npmjs.org/uqr/-/uqr-0.1.2.tgz",
      "integrity": "sha512-MJu7ypHq6QasgF5YRTjqscSzQp/W11zoUk6kvmlH+fmWEs63Y0Eib13hYFwAzagRJcVY8WVnlV+eBDUGMJ5IbA=="
    },
    "node_modules/uri-js": {
      "version": "4.4.1",
      "resolved": "https://registry.npmjs.org/uri-js/-/uri-js-4.4.1.tgz",
      "integrity": "sha512-7rKUyy33Q1yc98pQ1DAmLtwX109F7TIfWlW1Ydo8Wl1ii1SeHieeh0HHfPeL2fMXK6z0s8ecKs9frCuLJvndBg==",
      "dev": true,
      "dependencies": {
        "punycode": "^2.1.0"
      }
    },
    "node_modules/use-sync-external-store": {
      "version": "1.2.0",
      "resolved": "https://registry.npmjs.org/use-sync-external-store/-/use-sync-external-store-1.2.0.tgz",
      "integrity": "sha512-eEgnFxGQ1Ife9bzYs6VLi8/4X6CObHMw9Qr9tPY43iKwsPw8xE8+EFsf/2cFZ5S3esXgpWgtSCtLNS41F+sKPA==",
      "peerDependencies": {
        "react": "^16.8.0 || ^17.0.0 || ^18.0.0"
      }
    },
    "node_modules/utf-8-validate": {
      "version": "5.0.10",
      "resolved": "https://registry.npmjs.org/utf-8-validate/-/utf-8-validate-5.0.10.tgz",
      "integrity": "sha512-Z6czzLq4u8fPOyx7TU6X3dvUZVvoJmxSQ+IcrlmagKhilxlhZgxPK6C5Jqbkw1IDUmFTM+cz9QDnnLTwDz/2gQ==",
      "hasInstallScript": true,
      "optional": true,
      "dependencies": {
        "node-gyp-build": "^4.3.0"
      },
      "engines": {
        "node": ">=6.14.2"
      }
    },
    "node_modules/util-deprecate": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/util-deprecate/-/util-deprecate-1.0.2.tgz",
      "integrity": "sha512-EPD5q1uXyFxJpCrLnCc1nHnq3gOa6DZBocAIiI2TaSCA7VCJ1UJDMagCzIkXNsUYfD1daK//LTEQ8xiIbrHtcw=="
    },
    "node_modules/uuid": {
      "version": "8.3.2",
      "resolved": "https://registry.npmjs.org/uuid/-/uuid-8.3.2.tgz",
      "integrity": "sha512-+NYs2QeMWy+GWFOEm9xnn6HCDp0l7QBD7ml8zLUmJ+93Q5NF0NocErnwkTkXVFNiX3/fpC6afS8Dhb/gz7R7eg==",
      "bin": {
        "uuid": "dist/bin/uuid"
      }
    },
    "node_modules/uuidv4": {
      "version": "6.2.13",
      "resolved": "https://registry.npmjs.org/uuidv4/-/uuidv4-6.2.13.tgz",
      "integrity": "sha512-AXyzMjazYB3ovL3q051VLH06Ixj//Knx7QnUSi1T//Ie3io6CpsPu9nVMOx5MoLWh6xV0B9J0hIaxungxXUbPQ==",
      "deprecated": "Package no longer supported. Contact Support at https://www.npmjs.com/support for more info.",
      "dependencies": {
        "@types/uuid": "8.3.4",
        "uuid": "8.3.2"
      }
    },
    "node_modules/valtio": {
      "version": "1.11.2",
      "resolved": "https://registry.npmjs.org/valtio/-/valtio-1.11.2.tgz",
      "integrity": "sha512-1XfIxnUXzyswPAPXo1P3Pdx2mq/pIqZICkWN60Hby0d9Iqb+MEIpqgYVlbflvHdrp2YR/q3jyKWRPJJ100yxaw==",
      "dependencies": {
        "proxy-compare": "2.5.1",
        "use-sync-external-store": "1.2.0"
      },
      "engines": {
        "node": ">=12.20.0"
      },
      "peerDependencies": {
        "@types/react": ">=16.8",
        "react": ">=16.8"
      },
      "peerDependenciesMeta": {
        "@types/react": {
          "optional": true
        },
        "react": {
          "optional": true
        }
      }
    },
    "node_modules/viem": {
      "version": "2.21.38",
      "resolved": "https://registry.npmjs.org/viem/-/viem-2.21.38.tgz",
      "integrity": "sha512-MxhURy+F3eRtxkOoj7YdJTStJxqnWcP0MQZycVsxsVB4eZLKZPZfh7AgpfPjWHmPHmeVZcOqaGzFTmuPpqp06w==",
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/wevm"
        }
      ],
      "dependencies": {
        "@adraffy/ens-normalize": "1.11.0",
        "@noble/curves": "1.6.0",
        "@noble/hashes": "1.5.0",
        "@scure/bip32": "1.5.0",
        "@scure/bip39": "1.4.0",
        "abitype": "1.0.6",
        "isows": "1.0.6",
        "webauthn-p256": "0.0.10",
        "ws": "8.18.0"
      },
      "peerDependencies": {
        "typescript": ">=5.0.4"
      },
      "peerDependenciesMeta": {
        "typescript": {
          "optional": true
        }
      }
    },
    "node_modules/viem/node_modules/@scure/bip32": {
      "version": "1.5.0",
      "resolved": "https://registry.npmjs.org/@scure/bip32/-/bip32-1.5.0.tgz",
      "integrity": "sha512-8EnFYkqEQdnkuGBVpCzKxyIwDCBLDVj3oiX0EKUFre/tOjL/Hqba1D6n/8RcmaQy4f95qQFrO2A8Sr6ybh4NRw==",
      "dependencies": {
        "@noble/curves": "~1.6.0",
        "@noble/hashes": "~1.5.0",
        "@scure/base": "~1.1.7"
      },
      "funding": {
        "url": "https://paulmillr.com/funding/"
      }
    },
    "node_modules/viem/node_modules/@scure/bip39": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/@scure/bip39/-/bip39-1.4.0.tgz",
      "integrity": "sha512-BEEm6p8IueV/ZTfQLp/0vhw4NPnT9oWf5+28nvmeUICjP99f4vr2d+qc7AVGDDtwRep6ifR43Yed9ERVmiITzw==",
      "dependencies": {
        "@noble/hashes": "~1.5.0",
        "@scure/base": "~1.1.8"
      },
      "funding": {
        "url": "https://paulmillr.com/funding/"
      }
    },
    "node_modules/vite": {
      "version": "5.4.10",
      "resolved": "https://registry.npmjs.org/vite/-/vite-5.4.10.tgz",
      "integrity": "sha512-1hvaPshuPUtxeQ0hsVH3Mud0ZanOLwVTneA1EgbAM5LhaZEqyPWGRQ7BtaMvUrTDeEaC8pxtj6a6jku3x4z6SQ==",
      "dev": true,
      "dependencies": {
        "esbuild": "^0.21.3",
        "postcss": "^8.4.43",
        "rollup": "^4.20.0"
      },
      "bin": {
        "vite": "bin/vite.js"
      },
      "engines": {
        "node": "^18.0.0 || >=20.0.0"
      },
      "funding": {
        "url": "https://github.com/vitejs/vite?sponsor=1"
      },
      "optionalDependencies": {
        "fsevents": "~2.3.3"
      },
      "peerDependencies": {
        "@types/node": "^18.0.0 || >=20.0.0",
        "less": "*",
        "lightningcss": "^1.21.0",
        "sass": "*",
        "sass-embedded": "*",
        "stylus": "*",
        "sugarss": "*",
        "terser": "^5.4.0"
      },
      "peerDependenciesMeta": {
        "@types/node": {
          "optional": true
        },
        "less": {
          "optional": true
        },
        "lightningcss": {
          "optional": true
        },
        "sass": {
          "optional": true
        },
        "sass-embedded": {
          "optional": true
        },
        "stylus": {
          "optional": true
        },
        "sugarss": {
          "optional": true
        },
        "terser": {
          "optional": true
        }
      }
    },
    "node_modules/void-elements": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/void-elements/-/void-elements-3.1.0.tgz",
      "integrity": "sha512-Dhxzh5HZuiHQhbvTW9AMetFfBHDMYpo23Uo9btPXgdYP+3T5S+p+jgNy7spra+veYhBP2dCSgxR/i2Y02h5/6w==",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/wait-on": {
      "version": "7.0.1",
      "resolved": "https://registry.npmjs.org/wait-on/-/wait-on-7.0.1.tgz",
      "integrity": "sha512-9AnJE9qTjRQOlTZIldAaf/da2eW0eSRSgcqq85mXQja/DW3MriHxkpODDSUEg+Gri/rKEcXUZHe+cevvYItaog==",
      "dependencies": {
        "axios": "^0.27.2",
        "joi": "^17.7.0",
        "lodash": "^4.17.21",
        "minimist": "^1.2.7",
        "rxjs": "^7.8.0"
      },
      "bin": {
        "wait-on": "bin/wait-on"
      },
      "engines": {
        "node": ">=12.0.0"
      }
    },
    "node_modules/wait-on/node_modules/axios": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/axios/-/axios-0.27.2.tgz",
      "integrity": "sha512-t+yRIyySRTp/wua5xEr+z1q60QmLq8ABsS5O9Me1AsE5dfKqgnCFzwiCZZ/cGNd1lq4/7akDWMxdhVlucjmnOQ==",
      "dependencies": {
        "follow-redirects": "^1.14.9",
        "form-data": "^4.0.0"
      }
    },
    "node_modules/webauthn-p256": {
      "version": "0.0.10",
      "resolved": "https://registry.npmjs.org/webauthn-p256/-/webauthn-p256-0.0.10.tgz",
      "integrity": "sha512-EeYD+gmIT80YkSIDb2iWq0lq2zbHo1CxHlQTeJ+KkCILWpVy3zASH3ByD4bopzfk0uCwXxLqKGLqp2W4O28VFA==",
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/wevm"
        }
      ],
      "dependencies": {
        "@noble/curves": "^1.4.0",
        "@noble/hashes": "^1.4.0"
      }
    },
    "node_modules/webidl-conversions": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/webidl-conversions/-/webidl-conversions-3.0.1.tgz",
      "integrity": "sha512-2JAn3z8AR6rjK8Sm8orRC0h/bcl/DqL7tRPdGZ4I1CjdF+EaMLmYxBHyXuKL849eucPFhvBoxMsflfOb8kxaeQ=="
    },
    "node_modules/whatwg-url": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/whatwg-url/-/whatwg-url-5.0.0.tgz",
      "integrity": "sha512-saE57nupxk6v3HY35+jzBwYa0rKSy0XR8JSxZPwgLr7ys0IBzhGviA1/TUGJLmSVqs8pb9AnvICXEuOHLprYTw==",
      "dependencies": {
        "tr46": "~0.0.3",
        "webidl-conversions": "^3.0.0"
      }
    },
    "node_modules/which": {
      "version": "2.0.2",
      "resolved": "https://registry.npmjs.org/which/-/which-2.0.2.tgz",
      "integrity": "sha512-BLI3Tl1TW3Pvl70l3yq3Y64i+awpwXqsGBYWkkqMtnbXgrMD+yj7rhW0kuEDxzJaYXGjEW5ogapKNMEKNMjibA==",
      "dependencies": {
        "isexe": "^2.0.0"
      },
      "bin": {
        "node-which": "bin/node-which"
      },
      "engines": {
        "node": ">= 8"
      }
    },
    "node_modules/which-module": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/which-module/-/which-module-2.0.1.tgz",
      "integrity": "sha512-iBdZ57RDvnOR9AGBhML2vFZf7h8vmBjhoaZqODJBFWHVtKkDmKuHai3cx5PgVMrX5YDNp27AofYbAwctSS+vhQ=="
    },
    "node_modules/word-wrap": {
      "version": "1.2.5",
      "resolved": "https://registry.npmjs.org/word-wrap/-/word-wrap-1.2.5.tgz",
      "integrity": "sha512-BN22B5eaMMI9UMtjrGd5g5eCYPpCPDUy0FJXbYsaT5zYxjFOckS53SQDE3pWkVoWpHXVb3BrYcEN4Twa55B5cA==",
      "dev": true,
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/wrap-ansi": {
      "version": "6.2.0",
      "resolved": "https://registry.npmjs.org/wrap-ansi/-/wrap-ansi-6.2.0.tgz",
      "integrity": "sha512-r6lPcBGxZXlIcymEu7InxDMhdW0KDxpLgoFLcguasxCaJ/SOIZwINatK9KY/tf+ZrlywOKU0UDj3ATXUBfxJXA==",
      "dependencies": {
        "ansi-styles": "^4.0.0",
        "string-width": "^4.1.0",
        "strip-ansi": "^6.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/wrap-ansi-cjs": {
      "name": "wrap-ansi",
      "version": "7.0.0",
      "resolved": "https://registry.npmjs.org/wrap-ansi/-/wrap-ansi-7.0.0.tgz",
      "integrity": "sha512-YVGIj2kamLSTxw6NsZjoBxfSwsn0ycdesmc4p+Q21c5zPuZ1pl+NfxVdxPtdHvmNVOQ6XSYG4AUtyt/Fi7D16Q==",
      "dev": true,
      "dependencies": {
        "ansi-styles": "^4.0.0",
        "string-width": "^4.1.0",
        "strip-ansi": "^6.0.0"
      },
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/chalk/wrap-ansi?sponsor=1"
      }
    },
    "node_modules/wrappy": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/wrappy/-/wrappy-1.0.2.tgz",
      "integrity": "sha512-l4Sp/DRseor9wL6EvV2+TuQn63dMkPjZ/sp9XkghTEbV9KlPS1xUsZ3u7/IQO4wxtcFB4bgpQPRcR3QCvezPcQ=="
    },
    "node_modules/ws": {
      "version": "8.18.0",
      "resolved": "https://registry.npmjs.org/ws/-/ws-8.18.0.tgz",
      "integrity": "sha512-8VbfWfHLbbwu3+N6OKsOMpBdT4kXPDDB9cJk2bJ6mh9ucxdlnNvH1e+roYkKmN9Nxw2yjz7VzeO9oOz2zJ04Pw==",
      "engines": {
        "node": ">=10.0.0"
      },
      "peerDependencies": {
        "bufferutil": "^4.0.1",
        "utf-8-validate": ">=5.0.2"
      },
      "peerDependenciesMeta": {
        "bufferutil": {
          "optional": true
        },
        "utf-8-validate": {
          "optional": true
        }
      }
    },
    "node_modules/xtend": {
      "version": "4.0.2",
      "resolved": "https://registry.npmjs.org/xtend/-/xtend-4.0.2.tgz",
      "integrity": "sha512-LKYU1iAXJXUgAXn9URjiu+MWhyUXHsvfp7mcuYm9dSUKK0/CjtrUwFAxD82/mCWbtLsGjFIad0wIsod4zrTAEQ==",
      "engines": {
        "node": ">=0.4"
      }
    },
    "node_modules/y18n": {
      "version": "4.0.3",
      "resolved": "https://registry.npmjs.org/y18n/-/y18n-4.0.3.tgz",
      "integrity": "sha512-JKhqTOwSrqNA1NY5lSztJ1GrBiUodLMmIZuLiDaMRJ+itFd+ABVE8XBjOvIWL+rSqNDC74LCSFmlb/U4UZ4hJQ=="
    },
    "node_modules/yallist": {
      "version": "3.1.1",
      "resolved": "https://registry.npmjs.org/yallist/-/yallist-3.1.1.tgz",
      "integrity": "sha512-a4UGQaWPH59mOXUYnAG2ewncQS4i4F43Tv3JoAM+s2VDAmS9NsK8GpDMLrCHPksFT7h3K6TOoUNn2pb7RoXx4g==",
      "dev": true
    },
    "node_modules/yaml": {
      "version": "2.6.0",
      "resolved": "https://registry.npmjs.org/yaml/-/yaml-2.6.0.tgz",
      "integrity": "sha512-a6ae//JvKDEra2kdi1qzCyrJW/WZCgFi8ydDV+eXExl95t+5R+ijnqHJbz9tmMh8FUjx3iv2fCQ4dclAQlO2UQ==",
      "dev": true,
      "bin": {
        "yaml": "bin.mjs"
      },
      "engines": {
        "node": ">= 14"
      }
    },
    "node_modules/yargs": {
      "version": "15.4.1",
      "resolved": "https://registry.npmjs.org/yargs/-/yargs-15.4.1.tgz",
      "integrity": "sha512-aePbxDmcYW++PaqBsJ+HYUFwCdv4LVvdnhBy78E57PIor8/OVvhMrADFFEDh8DHDFRv/O9i3lPhsENjO7QX0+A==",
      "dependencies": {
        "cliui": "^6.0.0",
        "decamelize": "^1.2.0",
        "find-up": "^4.1.0",
        "get-caller-file": "^2.0.1",
        "require-directory": "^2.1.1",
        "require-main-filename": "^2.0.0",
        "set-blocking": "^2.0.0",
        "string-width": "^4.2.0",
        "which-module": "^2.0.0",
        "y18n": "^4.0.0",
        "yargs-parser": "^18.1.2"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/yargs-parser": {
      "version": "18.1.3",
      "resolved": "https://registry.npmjs.org/yargs-parser/-/yargs-parser-18.1.3.tgz",
      "integrity": "sha512-o50j0JeToy/4K6OZcaQmW6lyXXKhq7csREXcDwk2omFPJEwUNOVtJKvmDr9EI1fAJZUyZcRF7kxGBWmRXudrCQ==",
      "dependencies": {
        "camelcase": "^5.0.0",
        "decamelize": "^1.2.0"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/yargs/node_modules/find-up": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/find-up/-/find-up-4.1.0.tgz",
      "integrity": "sha512-PpOwAdQ/YlXQ2vj8a3h8IipDuYRi3wceVQQGYWxNINccq40Anw7BlsEXCMbt1Zt+OLA6Fq9suIpIWD0OsnISlw==",
      "dependencies": {
        "locate-path": "^5.0.0",
        "path-exists": "^4.0.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/yargs/node_modules/locate-path": {
      "version": "5.0.0",
      "resolved": "https://registry.npmjs.org/locate-path/-/locate-path-5.0.0.tgz",
      "integrity": "sha512-t7hw9pI+WvuwNJXwk5zVHpyhIqzg2qTlklJOf0mVxGSbe3Fp2VieZcduNYjaLDoy6p9uGpQEGWG87WpMKlNq8g==",
      "dependencies": {
        "p-locate": "^4.1.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/yargs/node_modules/p-limit": {
      "version": "2.3.0",
      "resolved": "https://registry.npmjs.org/p-limit/-/p-limit-2.3.0.tgz",
      "integrity": "sha512-//88mFWSJx8lxCzwdAABTJL2MyWB12+eIY7MDL2SqLmAkeKU9qxRvWuSyTjm3FUmpBEMuFfckAIqEaVGUDxb6w==",
      "dependencies": {
        "p-try": "^2.0.0"
      },
      "engines": {
        "node": ">=6"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/yargs/node_modules/p-locate": {
      "version": "4.1.0",
      "resolved": "https://registry.npmjs.org/p-locate/-/p-locate-4.1.0.tgz",
      "integrity": "sha512-R79ZZ/0wAxKGu3oYMlz8jy/kbhsNrS7SKZ7PxEHBgJ5+F2mtFW2fK2cOtBh1cHYkQsbzFV7I+EoRKe6Yt0oK7A==",
      "dependencies": {
        "p-limit": "^2.2.0"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/yocto-queue": {
      "version": "0.1.0",
      "resolved": "https://registry.npmjs.org/yocto-queue/-/yocto-queue-0.1.0.tgz",
      "integrity": "sha512-rVksvsnNCdJ/ohGc6xgPwyN8eheCxsiLM8mxuE/t/mOVqJewPuO1miLpTHQiRgTKCLexL4MeAFVagts7HmNZ2Q==",
      "dev": true,
      "engines": {
        "node": ">=10"
      },
      "funding": {
        "url": "https://github.com/sponsors/sindresorhus"
      }
    },
    "node_modules/zustand": {
      "version": "4.5.5",
      "resolved": "https://registry.npmjs.org/zustand/-/zustand-4.5.5.tgz",
      "integrity": "sha512-+0PALYNJNgK6hldkgDq2vLrw5f6g/jCInz52n9RTpropGgeAf/ioFUCdtsjCqu4gNhW9D01rUQBROoRjdzyn2Q==",
      "dependencies": {
        "use-sync-external-store": "1.2.2"
      },
      "engines": {
        "node": ">=12.7.0"
      },
      "peerDependencies": {
        "@types/react": ">=16.8",
        "immer": ">=9.0.6",
        "react": ">=16.8"
      },
      "peerDependenciesMeta": {
        "@types/react": {
          "optional": true
        },
        "immer": {
          "optional": true
        },
        "react": {
          "optional": true
        }
      }
    },
    "node_modules/zustand/node_modules/use-sync-external-store": {
      "version": "1.2.2",
      "resolved": "https://registry.npmjs.org/use-sync-external-store/-/use-sync-external-store-1.2.2.tgz",
      "integrity": "sha512-PElTlVMwpblvbNqQ82d2n6RjStvdSoNe9FG28kNfz3WiXilJm4DdNkEzRhCZuIDwY8U08WVihhGR5iRqAwfDiw==",
      "peerDependencies": {
        "react": "^16.8.0 || ^17.0.0 || ^18.0.0"
      }
    }
  }
}

```
