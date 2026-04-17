# Sphero Bolt

## Prerequisites
- Ensure you have Node.js installed on your machine.
- Install the Sphero SDK: `npm install sphero`

## Quick Start
1. Clone the repository:
   ```bash
   git clone https://github.com/Willxxx7/SpheroBolt.git
   cd SpheroBolt
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Run the project:
   ```bash
   node index.js
   ```

## Code Examples
### Basic Movement
```javascript
const Sphero = require('sphero');
const sphero = Sphero('YOUR_SPHERO_SERIAL');

sphero.color('red');
sphero.roll(100, 90); // Roll forward at 100 speed for 90 degrees
```

## Project Structure
- `index.js`: Main entry point of the application.
- `lib/`: Contains library files for additional functionality.
- `package.json`: Contains project metadata and dependencies.

## Troubleshooting
- **Issue with Serial Connection:** Ensure your Sphero is charged and powered on.
- **NPM Install Error:** Try clearing the npm cache: `npm cache clean --force`

## Formatting Improvements
This README now contains organized sections for better readability and usability. Use the above guide to quickly get started with your project!