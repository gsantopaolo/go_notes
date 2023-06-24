# Cofigure Go and VS Code
(update Jun 2023)
Before you get started, ensure that you have the following prerequisites:

1. You have Go installed on your computer. As of my knowledge cutoff in September 2021, you can download Go from https://golang.org/dl/.
2. You have Visual Studio Code installed on your computer. You can download it from https://code.visualstudio.com/.

Here are the step-by-step instructions to set up Visual Studio Code for Go development:

1. **Install the Go Extension for Visual Studio Code**:
   - Open Visual Studio Code.
   - Click on the Extensions view icon on the Sidebar (or press `Ctrl+Shift+X` to open it).
   - In the Extensions view, type 'Go' into the search form.
   - Find the Go extension by Google and click the Install button.

2. **Initialize your Go project**:
   - Create a new folder where you want your Go project to live.
   - Open Visual Studio Code.
   - Go to `File > Open Folder...` and select the folder you just created.
  
   As of Go 1.16, module-aware mode is enabled by default, which means Go expects a `go.mod` file in the project directory or any parent directory.

   1. Open the Terminal in Visual Studio Code.

   2. Navigate to the directory of your Go project. You can do this with the `cd` command. For example:

   ```bash
   cd /path/to/your/project
   ```

   Replace `/path/to/your/project` with the path to your Go project directory.

   3. Once you're in your project directory, initialize a new Go module by typing:

   ```bash
   go mod init <module_name>
   ```

   Replace `<module_name>` with the name you want for your module. This is typically the repository location if you're planning on pushing your code to a remote repository. For local projects, you can use any name.

   Here's an example:

   ```bash
   go mod init github.com/username/myproject
   ```

   If you're not planning to publish your package or don't have a specific structure in mind, it's fine to use a placeholder name. For example:

   ```bash
   go mod init example.com/mymodule
   ```

4. After you've initialized the module, try running your `go build` command again:

   ```bash
   go build -o ironctl
   ```

4. **Write the Go code**:
   - Create a new file in your project folder (you can call it `main.go`).
   - Copy and paste the Go code into `main.go`.

5. **Configure the Go Environment**:
   - Open the Terminal in Visual Studio Code (you can do this by going to `View > Terminal` or pressing `Ctrl+` backtick).
   - In the Terminal, type `go env` to print Go's environment information.
   - To change an environment variable, you can use the `go env -w` command. For example, to change the `GOPATH`, you would type `go env -w GOPATH=/my/new/gopath`. 
   
   
   


6. **Build the Go code**:
   - Open the Terminal in Visual Studio Code (you can do this by going to `View > Terminal` or pressing `Ctrl+` backtick).
   - In the Terminal, navigate to the directory where your `main.go` file is located.
   - Type `go build` to compile the code. This will create an executable file in the same directory.

7. **Run the Go code**:
   - In the Terminal, you can run the code by typing `./<your-executable>`. Replace `<your-executable>` with the name of the executable file created in the previous step. On Windows, the file will have a `.exe` extension.

8. **Debug the Go code**:
   - Set a breakpoint in your code by clicking in the left margin of the code editor.
   - Press `F5` to start debugging. Visual Studio Code will run your program until it hits the breakpoint.

Go uses packages, not namespaces. Each Go file starts with a `package <name>` declaration. In this case, the package is `main`, which is the default name for a standalone executable in Go.

# Package and Module
In Go programming, the terms "package" and "module" have distinct meanings:

1. **Package**: A package in Go is a namespace that organizes a set of related files. It's a way to group related Go code together, forming a single unit. In simpler terms, it's like a library or code module in other languages. The name of the package is the same as the last element of the import path. For example, the "fmt" package provides functionalities for formatted I/O with functions like `fmt.Println()`. A package is chosen to compile along with the program based on its import paths. Each Go file starts with the package name at the top, which is used to identify what package the file belongs to, like `package main`.

2. **Module**: A Module is a collection of related Go packages that are released, versioned, and distributed together. Modules are how Go manages dependencies. Before Go 1.11, there was no true concept of a module. Go 1.11 introduced experimental support for modules, and it has been the official dependency management solution since Go 1.13. A module is defined by a `go.mod` file in the root directory of the hierarchy, and this file defines the module path, which is the import path prefix for all packages within the module. The `go.mod` file also defines the specific versions of other modules that should be used when resolving imports during a build, which ensures repeatable builds.

In summary, you can think of a package as a single library or utility, and a module as a collection of related packages distributed together, potentially with version information.
A package is a directory of .go files, and it is the basic building block of a Go program. Packages help to organize code into reusable components.

On the other side, a module is a collection of packages with built-in dependencies and versioning. A module comes with two additional files go.mod and go.sum.
