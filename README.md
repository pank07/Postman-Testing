# Postman-Testing
```
// Parse the JSON response
const responseData = pm.response.json();

// 1️⃣ Check the status code is 200 OK
pm.test("Status code is 200", () => {
    pm.response.to.have.status(200);
});

// 2️⃣ Check that 'data' object exists
pm.test("Response has data object", () => {
    pm.expect(responseData).to.have.property('data');
});

// 3️⃣ Validate that first_name and last_name are strings
pm.test("First and Last name are strings", () => {
    const user = responseData.data;
    pm.expect(user).to.have.property('first_name');
    pm.expect(user.first_name).to.be.a('string');

    pm.expect(user).to.have.property('last_name');
    pm.expect(user.last_name).to.be.a('string');
});

// 4️⃣ Optional: Check email format
pm.test("Email is valid format", () => {
    const email = responseData.data.email;
    pm.expect(email).to.match(/^[^\s@]+@[^\s@]+\.[^\s@]+$/);
});
```
