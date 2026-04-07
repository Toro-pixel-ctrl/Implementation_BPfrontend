# Sentry Setup & Guidelines

This guide covers the standard integration of Sentry for error tracking and feedback loops in the **Implementation_BPfrontend** project.

## 🎯 Purpose
Sentry is our primary tool for:
1. **Error Tracking:** Automatically capturing runtime errors, exceptions, and unhandled promise rejections.
2. **Performance Monitoring:** Tracking page load speeds and identifying bottlenecks.
3. **User Feedback:** Giving users an option to submit a report if the application crashes.

## ⚙️ Basic Integration Checklist
1. **Create Account/Project:** Obtain your project's DSN (Data Source Name) from the Sentry dashboard.
2. **Integrate SDK:** Include the Sentry Javascript SDK into `index.html` or main app entry point.
3. **Initialize:** Call `Sentry.init({ dsn: "YOUR_DSN_HERE" })` at the earliest possible point in the code.
4. **Feedback Widget:** If desired, enable the Sentry User Feedback widget for user crash reports.

## 🧪 Verification
Always verify the setup by triggering a deliberate error in development:
```javascript
setTimeout(() => {
  throw new Error("Sentry Integration Test");
}, 2000);
```
Ensure the error appears in the Sentry dashboard before declaring the setup complete.
