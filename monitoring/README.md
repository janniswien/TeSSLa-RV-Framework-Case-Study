# Monitoring UI and Server
This [Nuxt](https://nuxt.com) application implements a user interface and an API that lets you manage logged traces and execute the Runtime Verification monitor on them. 

Please note that the TeSSLa monitor requires access to the JDK/JRE 21 via the `java` command. Please make sure to [install Java](https://www.oracle.com/de/java/technologies/downloads/#java21) and add it to the PATH of the application's runtime.

Some exemplary log traces are already stored in the `trace-files` directory and can be used for offline verification.

## API Methods
The following API methods are exposed by the application:

* `GET /api/monitors/{sessionId}`: Execute the monitor and receive its final verdict for a given session. May take a long time to respond depending on the JVM's resources.
* `GET /api/sessions`: Retrieve all available sessions and their IDs
* `POST /api/sessions`: Create a new session ID. A trace can only be stored and verified if its associated session ID is known.
* `DELETE /api/sessions/{sessionId}`: Removes a session and its corresponding log trace. Cannot be reverted.
* `GET /api/traces/{sessionId}`: Retrieve all log events stored for a given session id.
* `POST /api/traces/{sessionId}/overwrite`: Stores a single log trace line by overwriting all previously stored lines.
* `POST /api/traces/{sessionId}/append`: Stores a single log trace line by adding it to the end of all previously stored lines.


Look at the [Nuxt documentation](https://nuxt.com/docs/getting-started/introduction) to learn more.

## Nuxt-Specific Setup and Deployment
### Setup

Make sure to install dependencies:

```bash
# npm
npm install

# pnpm
pnpm install

# yarn
yarn install

# bun
bun install
```

### Development Server

Start the development server on `http://localhost:3000`:

```bash
# npm
npm run dev

# pnpm
pnpm dev

# yarn
yarn dev

# bun
bun run dev
```

### Production

Build the application for production:

```bash
# npm
npm run build

# pnpm
pnpm build

# yarn
yarn build

# bun
bun run build
```

Locally preview production build:

```bash
# npm
npm run preview

# pnpm
pnpm preview

# yarn
yarn preview

# bun
bun run preview
```

Check out the [deployment documentation](https://nuxt.com/docs/getting-started/deployment) for more information.
