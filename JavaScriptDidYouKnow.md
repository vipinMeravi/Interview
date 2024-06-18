=> import needs curly braces for named exports and does not need them for the default one.
Named export	        Default export
export class User {...}	export default class User {...}
import {User} from ...	import User from ...

=> JSX is not a valid javascript. Browsers cannot read it directly. Therefore, during the build process, JSX get transformed into regular JavaScript. This is usually done by a tool like Babel. 

=> Dependency Array Variations
1. No Dependency Array: The effect runs after every render.
2. Empty Dependency Array: The effect runs only once, after the initial render.
3. Specific Dependencies: The effect runs only when specified dependencies change.