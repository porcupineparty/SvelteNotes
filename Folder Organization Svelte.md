
## Where To Store Components

1. Components that are used accross your project are stored in `src/lib/components` file
2. Components that are only used for one route or page, you store that component in the page file that is being served. For example if you have a +page.svelte file with the route being /ui you would store it in the root of the /ui directory and import it into the +page.svelte file in the ***SAME*** directory.
3. In more structured projects, you might separate your components based on their purpose. For example, you might have a design system folder (`ui`, `elements`) that stores atomic components like buttons, inputs, and modals.
/src
  └── /lib
        ├── /ui
        │     ├── Button.svelte
        │     └── Modal.svelte
        └── /components
              ├── Navbar.svelte
              └── Footer.svelte

- **`src/lib/ui`**: This would store smaller, atomic components like buttons or form elements that can be used across the application.
- **`src/lib/components`**: This would store more complex or composite components like headers, footers, or layout sections.
### Summary of Component Organization:

- **Shared, reusable components**: `src/lib/components` or `src/lib/ui`.
- **Route-specific components**: `src/routes/[route-name]/[Component].svelte`.
- **Design system or atomic components**: `src/lib/ui` or `src/lib/elements`.