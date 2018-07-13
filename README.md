# Meteor-SSR

Annonce post here: https://forums.meteor.com/t/ssr-with-user-data-example/44018

An isomorphic (universal) Meteor starter project with Viewmodel-react for declarative components and state management.
Viewmodel is easy-to-use (similar to Vue), and fallback on React if needed.

SSR “just works”. You write your app and it’s rendered on server-side correctly whether a component uses data or not.
No need to put data/state on the initial HTML render.
User data is SSR’d normally. Again, just write the app.
Admin section (/admin) is lazily loaded (not part of the main bundle).

This starter has SSR, isomorphic routing built-in, and will render the initial component's states directly in both client and server (first server-rendering, then client rehydration).
It is also highly extendable using Meteor's capabilities. 
It doesn't rely on many dependancies but can already do a lot.

Technology used 
-------------
If you need to change the stack or add dependencies

1. [Meteor](https://www.meteor.com/) for isomorphic database reactivity, isomorphic builds, SSR, exact code splitting, reactive data, user accounts, security...
2. [Viewmodel](https://viewmodel.org/) For components,internal state management,client validation, bindings between state and view... 
3. [React](https://facebook.github.io/react/) For the underlying layer of Viewmodel. It can be changed to [Inferno](https://github.com/infernojs/inferno) according to Viewmodel, and this would imply some changes in this starter.
4. [React router](https://github.com/kriasoft/universal-router) and [History](https://github.com/browserstate/history.js/) to provide an [easy-to-use](https://github.com/kriasoft/universal-router/issues/80), isomorphic router.
5. Test suite for Viewmodel and React: enzyme, jest... See [Viewmodel](https://viewmodel.org/) documentation for testing
6. [Debugging tool for Viewmodel](https://medium.com/@manueldeleon_94284/viewmodel-explorer-a-debugging-tool-3833403c3821): viewmodel-react-explorer component is included in the < App / > component, and let you play with the states of components


Installation
-------------
1. [Install Meteor](https://www.meteor.com/install)
2. In the command line, type: `git clone https://github.com/ManuelDeLeon/meteor-ssr.git` . Your folder must now be created
3. Go in this folder from the command line: `cd meteor-ssr`
4. `meteor update` (if needed)
5. `meteor npm install` (if needed)
6. `meteor npm update --save` (if needed)

`PROTIP:` If Meteor's builder gets stuck in the process, you can try to press Ctrl+C to abort some (sometime invisible) tasks and resume installation.
Pressing Ctrl+C twice will abort the run. If you do that, type `meteor` again.



Run
-------------
`meteor`

Then open your localhost: http://localhost:3000/


Folder structure
-------------
The full architecture follows [Meteor's file and folder structure](https://guide.meteor.com/structure.html)

`/ui` 
This folder contains isomorphic code, used by client and server.
This folder contains all ViewModel-react components.

`/client` 
Client-only code

`/client_server` 
This folder contains isomorphic code, used by client and server.
Contains Routes and Collections.

`/server` 
Server-only code

Caveats
-------------
- I forked react accounts ui and basic because they had errors and it was a lot easier to fix those than doing it from scratch.
- It’s technically possible for a user to pull the admin screen but they wouldn’t be able to view or modify admin data.
- It’s using ReactDOM.hydrate but that’s just the new name for .render(). By “hydrate” people typically mean injecting the initial state on the HTML and using it to render the state. That isn’t needed here.
- There’s some code duplication in the components. I felt that drying an example would make it less readable.


