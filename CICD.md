# CI/CD

## Prerequisites software

- [Nodejs](#nodejs)
- [Make](#make)
- [Python3](#python3)
- [Jenkins](#jenkins)

---

### nodejs

Nodejs version 20

- Macos & Windows: <https://nodejs.org/en/download/package-manager>
- Ubuntu:

  ```sh
  sudo apt update
  sudo apt install nodejs
  ```

Checking it work

```sh
node -v
```

### Make

- Macos: it work by default
- Windows: 2 options
  - [Directly download](https://gnuwin32.sourceforge.net/packages/make.htm)
  - Using [Chocolatey](https://chocolatey.org/install)

    ```sh
    choco install make
    ```

- Ubuntu:

    ```sh
    apt-get install build-essential
    ```

Checking it work

```sh
make -v
```

---

### Python3

- Macos:

    ```sh
    brew install python3
    ```

- Windows: <https://www.python.org/downloads/windows/>
- Ubuntu:

    ```sh
    sudo apt update
    sudo apt install python3
    ```

Checking it work

```sh
python3 -V
```

---

### Jenkins

Install with Long Term Support(LTS) release

- Macos: <https://www.jenkins.io/doc/book/installing/macos/>
- Windows: <https://www.jenkins.io/doc/book/installing/windows/>
- Ubuntu: <https://www.jenkins.io/doc/book/installing/linux/#debianubuntu>

Checking it work go to <http://localhost:8080>

If not work maybe check Java have been installed, or check path java_home
