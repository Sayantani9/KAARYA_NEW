const API_URL = "http://localhost:4000/api";


// -------------------------
// TEST BACKEND
// -------------------------

async function testAPI() {

    const status = document.getElementById("apiStatus");

    try {

        const response = await fetch(`${API_URL}/tasks`);

        const data = await response.json();

        console.log(data);

        status.textContent = "Backend connection successful.";

    } catch (error) {

        console.error(error);

        status.textContent =
            "Backend connection failed.";

    }
}


// -------------------------
// LOGIN
// -------------------------

const loginForm =
    document.getElementById("loginForm");


loginForm.addEventListener("submit", async (event) => {

    event.preventDefault();

    const email =
        document.getElementById("email").value;

    const password =
        document.getElementById("password").value;

    const status =
        document.getElementById("loginStatus");


    try {

        const response = await fetch(
            `${API_URL}/auth/login`,
            {
                method: "POST",

                headers: {
                    "Content-Type": "application/json"
                },

                body: JSON.stringify({
                    email,
                    password
                })
            }
        );


        const data = await response.json();


        if (!response.ok) {

            status.textContent =
                data.message || "Login failed.";

            return;
        }


        localStorage.setItem(
            "kaaryaToken",
            data.token
        );


        localStorage.setItem(
            "kaaryaUser",
            JSON.stringify(data.user)
        );


        status.textContent =
            `Welcome ${data.user.name}!`;

        console.log("LOGIN SUCCESS:", data);


    } catch (error) {

        console.error(error);

        status.textContent =
            "Could not connect to backend.";

    }

});

