1. A while later, the user's JWT expires and the user clicks on their shopping cart again. The browser requests the shopping cart from the application backend and sends the JWT and refresh token to the application backend
1. The application backend verifies the JWT and realizes it is expired. Since the browser also sent across the refresh token, the application backend calls the JWT refresh API in FusionAuth with the refresh token.
1. FusionAuth looks up the refresh token and returns a new JWT
1. The application backend responds with the user's shopping cart HTML, CSS & JavaScript that the browser renders. It also includes the new JWT as a cookie that replaces the old JWT in the browser