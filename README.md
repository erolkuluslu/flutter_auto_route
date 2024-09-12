
# Flutter Navigation and Routing Example

This Flutter project demonstrates how to handle navigation and routing in a Flutter application. It includes login, sign-up, and admin screens with a structured approach to navigating between them, managing user authentication, and implementing custom routes using the `auto_route` package.

## Features

- **User Authentication**: Handles login and sign-up forms.
- **Admin Panel**: Includes routes for user management and message handling within an admin dashboard.
- **Navigation and Routing**: Implements nested routes and parameter passing between screens using `auto_route`.
- **Route Guards**: Prevents unauthorized users from accessing specific routes.
- **Error Handling**: Provides error handling for undefined routes.

## Project Structure

The project is divided into several main folders:

- `lib/pages`: Contains the page widgets for the application.
  - `auth`: Manages authentication pages (Login, Sign-up).
  - `admin`: Contains the admin dashboard and related pages (User List, Messages).
  
- `lib/routes`: Contains the route definitions and constants used throughout the app.
  - `app_router.dart`: Defines the main routing configuration using `auto_route`.
  
- `lib/constants`: Stores constants like route paths and other static values.

## Dependencies

This project uses the following dependencies for routing and navigation:

- `auto_route`: Handles route generation and navigation.
- `auto_route_generator`: Used to generate routes.
- `build_runner`: Required to run the route generation.

To install the required packages, run the following command:

```bash
flutter pub add auto_route
flutter pub add --dev auto_route_generator build_runner
```

## How to Use

1. **Project Initialization**: 
   - The project begins with a login screen, where users can either log in or sign up.
   - After successful login, users are redirected to the admin panel.

2. **Admin Panel Navigation**:
   - The admin panel includes a drawer with two routes: `Dashboard` and `Users`.
   - Routes are dynamically loaded based on user interaction.
   
3. **Routing Configuration**:
   - Routes are configured in the `app_router.dart` file using the `auto_route` package.
   - A main route for authentication and nested routes for the admin panel are included.

4. **Route Guarding**:
   - The project includes logic to restrict navigation, ensuring users can't access the login screen again once they are authenticated.
   
## Example Code

### Route Configuration

```dart
@MaterialAutoRouter(
  replaceInRouteName: 'Page,Route',
  routes: <AutoRoute>[
    AutoRoute(page: AuthMainPage, initial: true, children: [
      AutoRoute(page: LoginPage),
      AutoRoute(page: SignUpPage),
    ]),
    AutoRoute(page: AdminMainPage, children: [
      AutoRoute(page: DashboardPage),
      AutoRoute(page: UsersPage),
    ]),
  ],
)
class $AppRouter {}
```

### Navigation Example

```dart
context.router.push(LoginRoute());
```

### Parameter Passing Example

```dart
context.router.push(UsersRoute(userId: '123'));
```

3. Generate the routes using `build_runner`:

   ```bash
   flutter pub run build_runner build --delete-conflicting-outputs
   ```

4. Run the project:

   ```bash
   flutter run
   ```

## Conclusion

This project demonstrates an efficient way to handle routing in Flutter using the `auto_route` package, enabling clean and maintainable code for navigating between different pages and screens in a Flutter app. 

---

Feel free to adjust the content as needed to better match your project!
