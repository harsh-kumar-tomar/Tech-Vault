The OAuth protocol enables websites or applications (Consumers) to access Protected Resources from a web service (Service Provider) via an API, without requiring Users to disclose their Service Provider credentials to the Consumers
An example use case is allowing printing service printer.example.com (the Consumer), to access private photos stored on photos.example.net (the Service Provider) without requiring Users to provide their photos.example.net credentials to printer.example.com.


**Components**
- **Resource Owner** – The user (you).
- **Consumer (Client)** – The app trying to access your data (e.g., a Twitter analytics tool).
- **Service Provider** – The API provider (e.g., Twitter).
- **Resource Server** – The server hosting user data (usually same as service provider).