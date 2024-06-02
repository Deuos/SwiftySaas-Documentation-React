# Public Routes & API Calls

##### Frontend Public Routes

In the React Router Dom paths, located in frontend/src/routes/RoutesPath.tsx, you can define any public route you want. Since user roles do not need to be checked, you can grant direct access to the React component.

Frontend Example: [https://swiftysaas.com/About](https://swiftysaas.com/About)

Example About Page:

```
import About from "./public/about/About";
<Route path='/About' element={<About />} />
```

##### Backend Public API Call

In your Express JS API calls, you can create a simple GET or POST request without any verification. This will return the necessary response without any authentication checks. Then, call it in index.ts to start using the route.

Backend Example: [https://api.swiftysaas.com/public/price](https://api.swiftysaas.com/public/price)

Example Get Price:

```
app.get('/public/price', async (_req: Request, res: Response) => {
    try {
	let price = .99  
        return res.status(200).json(price)

    } catch (error) {

        return res.status(500).json({ message: 'Internal Server Error' });
    }
})
export default publicPrice

```
