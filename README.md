# Post-Quantum Cryptography Testbed

This project provides a Docker-based testbed for experimenting with **Post-Quantum Cryptography (PQC)**. The aim is to explore and implement post-quantum algorithms in a controlled environment. This testbed is designed to support different quantum-safe cryptographic algorithms and evaluate their performance and security.

## 🚀 Features

- **Docker-based infrastructure** for easy setup and isolation.
- Integration of **quantum-resistant algorithms** such as **Kyber**, **NTRU**, and others.
- **Modular architecture** to easily add or remove cryptographic algorithms.
- Use of **Quantum-safe key exchange protocols**.
- Configuration for testing performance and scalability of PQC algorithms.
  
## 🛠️ Setup

### Prerequisites

- Docker and Docker Compose installed on your machine.
- A modern Linux/Unix-based system (Ubuntu preferred).
- Basic knowledge of cryptographic algorithms and quantum computing.

### Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/fobaty/pqc-testbed.git
    cd pqc-testbed
    ```

2. Build the Docker containers:

    ```bash
    docker-compose build
    ```

3. Start the testbed:

    ```bash
    docker-compose up
    ```

The services will now be running and ready for testing.

## 🧪 How to Use

1. Access the testbed services:
    - Use the `client` and `server` containers to simulate cryptographic exchanges.
    - Test quantum-safe encryption, key exchange, and other cryptographic functionalities.
  
2. For advanced configurations, modify the `docker-compose.yml` file and add your custom algorithms.

## 📊 Performance Metrics

The testbed also includes tools to measure the performance of various PQC algorithms, including:

- Latency
- Throughput
- Computational cost

## 🔐 Security Considerations

As post-quantum cryptography is still in its early stages, the testbed allows you to experiment with different algorithms and configurations to assess their security and efficiency.

## 📅 Future Work

- Integration with real-world applications for deployment of quantum-safe cryptography.
- Evaluation of more advanced PQC algorithms.
- Stress testing and benchmarking for high-volume environments.

## 🤝 Contributing

If you'd like to contribute, feel free to fork the repository and submit a pull request. Please ensure your contributions align with the project's goals and follow the coding guidelines.

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
