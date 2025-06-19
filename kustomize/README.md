# Kustomize Deployment Documentation

This project uses Kustomize to manage Kubernetes resources for deploying an application in different environments, specifically development and testing. 

## Project Structure

The project is organized into two main directories: `base` and `overlays`.

- **base**: Contains the core Kubernetes resource definitions that are common across environments.
  - `deployment.yaml`: Defines the deployment configuration for the application.
  - `service.yaml`: Defines the service configuration for the application.
  - `kustomization.yaml`: Kustomize configuration that references the deployment and service files.

- **overlays**: Contains environment-specific configurations.
  - **dev**: Contains configurations for the development environment.
    - `kustomization.yaml`: Kustomize configuration that references the base resources and includes development-specific settings.
    - `namespace.yaml`: Defines the namespace for the development environment.
  - **test**: Contains configurations for the testing environment.
    - `kustomization.yaml`: Kustomize configuration that references the base resources and includes testing-specific settings.
    - `namespace.yaml`: Defines the namespace for the testing environment.

## Usage

To deploy the application in a specific environment, navigate to the corresponding overlay directory and run the following command:

```bash
kubectl apply -k .
```

### Development Environment

To deploy to the development environment, use:

```bash
cd overlays/dev
kubectl apply -k .
```

### Testing Environment

To deploy to the testing environment, use:

```bash
cd overlays/test
kubectl apply -k .
```

## Notes

- Ensure that you have Kustomize installed and configured in your environment.
- Modify the `deployment.yaml` and `service.yaml` files in the `base` directory as needed to suit your application requirements.
- Customize the `kustomization.yaml` files in the overlays to include any patches or additional configurations specific to each environment.