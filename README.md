# Troubleshooting Build Errors

This guide provides solutions to common build errors encountered during the development process.

## Rust WASM Toolchain Not Installed

**Error**: build error: Rust WASM toolchain not installed, please install it!

**Solution**:

To resolve this issue, follow these steps:

1. Add the `wasm32-unknown-unknown` target using `rustup`:

    ```sh
    rustup target add wasm32-unknown-unknown
    ```

2. Update your cargo dependencies:

    ```sh
    cargo update
    ```

3. Clean your build environment:

    ```sh
    cargo clean
    ```

4. Rebuild your project:

    ```sh
    cargo build
    ```

---

## Unknown Feature `stdsimd`

**Error**: error[E0635]: unknown feature `stdsimd`

**Solution**:

This error may occur if there are multiple versions of `ahash` in your `Cargo.lock` file. To resolve it, follow these steps:

1. Confirm the presence of multiple `ahash` versions by running:

    ```sh
    cargo tree -i ahash
    ```

    If multiple versions are found (e.g., 0.7.x & 0.8.x), proceed with the following steps.

2. Remove your `Cargo.lock` file, or specifically remove one of the versions (preferably the older one).

3. Clean the `target/` folder:

    ```sh
    cargo clean
    ```

4. Build your project again:

    ```sh
    cargo build
    ```

Following these steps should resolve the specified errors and allow your build to proceed successfully.
