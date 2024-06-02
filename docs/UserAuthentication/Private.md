# Private Routes & API Calls

##### Frontend Private Routes

In the React Router Dom paths, located in `frontend/src/routes/RoutesPath.tsx`, you can define any private route you want. Since user roles need to be checked, you need to verify the user's role before granting access to the React component.

To achieve this, you'll need a React component that checks user roles, such as `frontend/src/routes/protected/profile/CheckProfile.tsx`. This component will check the user's role and grant access accordingly. You can define this check component in your routes path. For more information on handling role-based access control, refer to the [Supertoken Docs](https://supertokens.com/docs/emailpassword/user-roles/protecting-routes).

Example:

```
function CheckProfile() {
    let claimValue = Session.useClaimValue(UserRoleClaim);

    if (claimValue.loading) {
        return null;
    }

    let roles = claimValue.value;

    if (Array.isArray(roles) && (roles.includes("Paid") || (roles.includes("User")))) {

        return <Profile />;
    }
    else {

        return <Navigate to="/404" />;
    }
}
```

##### Backend Private API Calls

In your Express JS API calls, you can create a simple GET or POST request with verification. This will return the necessary response after checking for authentication. Then, call it in index.ts to start using the route.

To verify a session, you can simply add `verifySession()` from the SuperTokens Express framework to your request. This will verify the session claim sent by the frontend. If the session is invalid, it will send a 401 status code. Note that verifySession() only verifies the session and does not check for user roles.

Example:

```
app.get('/user/profile', verifySession(), async (req: Request, res: Response) => {
    try {
  
        return res.status(200).json({message: 'successful'})  
    } catch (error) {

        return res.status(500).json({ message: 'Internal Server Error' });
    }
})

```

**Role-Based Access Control**

For more in-depth user role claim requests, you can check user roles via a couple of methods as defined in the SuperTokens docs. Here's an example of how to handle it based on user roles:

You can check for included roles to verify if a user has a specific role, and handle accordingly. Examples of how to implement this can be found in `backend/src/services/stripe/payment.ts`.

Example:

```
app.get('/user/paided', verifySession(), async (req: Request, res: Response) => {
    try {
  	const roles = await req.session!.getClaimValue(UserRoles.UserRoleClaim);
	if (roles === undefined || roles.includes("User")) return res.status(404).json({ msg: "User has Not Paid! Please Pay Again." })

        return res.status(200).json({message: 'successful'})  
    } catch (error) {

        return res.status(500).json({ message: 'Internal Server Error' });
    }
})

```
