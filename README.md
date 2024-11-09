# LibreLol Frontend Website

This repository contains the source code for the LibreLol website, an open-source project aimed at providing a platform for sharing and discovering libre and open-source software.

## Development

To install and run the LibreLolWebsite locally, follow these steps:

1. Clone the repository:
    ```bash
    git clone https://git.libre.lol/librelol/FrontendWebsite.git
    ```
2. Navigate to the project directory:
    ```bash
    cd LibreLolWebsite
    ```
3. Install dependencies:
    ```bash
    npm install
    ```
4. Start the development server:
    ```bash
    npm run dev
    ```
5. Access the website at [http://localhost:3000](http://localhost:3000).

## Production

This website is designed to work on Coolify. If you want to test it in production mode, ensure you follow the development steps first. The production version runs on port 3030 to avoid conflicts with existing services.

1. Build the Docker image:
    ```bash
    docker build -t librelol-frontend .
    ```
2. Run the Docker container:
    ```bash
    docker run -p 3030:3030 librelol-frontend
    ```

## Contributing

We welcome contributions from the community! Create a pull request with a clear outline of the changes, and we’ll review them.

## License

This project is licensed under the DWTFYW License. See the [LICENSE](LICENSE) file for details.
