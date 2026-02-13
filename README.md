# ♕ BYU CS 240 Chess

This project demonstrates mastery of proper software design, client/server architecture, networking using HTTP and WebSocket, database persistence, unit testing, serialization, and security.

## 10k Architecture Overview

The application implements a multiplayer chess server and a command line chess client.

[![Sequence Diagram](10k-architecture.png)](https://sequencediagram.org/index.html#initialData=C4S2BsFMAIGEAtIGckCh0AcCGAnUBjEbAO2DnBElIEZVs8RCSzYKrgAmO3AorU6AGVIOAG4jUAEyzAsAIyxIYAERnzFkdKgrFIuaKlaUa0ALQA+ISPE4AXNABWAexDFoAcywBbTcLEizS1VZBSVbbVc9HGgnADNYiN19QzZSDkCrfztHFzdPH1Q-Gwzg9TDEqJj4iuSjdmoMopF7LywAaxgvJ3FC6wCLaFLQyHCdSriEseSm6NMBurT7AFcMaWAYOSdcSRTjTka+7NaO6C6emZK1YdHI-Qma6N6ss3nU4Gpl1ZkNrZwdhfeByy9hwyBA7mIT2KAyGGhuSWi9wuc0sAI49nyMG6ElQQA)

## Modules

The application has three modules.

- **Client**: The command line program used to play a game of chess over the network.
- **Server**: The command line program that listens for network requests from the client and manages users and games.
- **Shared**: Code that is used by both the client and the server. This includes the rules of chess and tracking the state of a game.

## Starter Code

As you create your chess application you will move through specific phases of development. This starts with implementing the moves of chess and finishes with sending game moves over the network between your client and server. You will start each phase by copying course provided [starter-code](starter-code/) for that phase into the source code of the project. Do not copy a phases' starter code before you are ready to begin work on that phase.

## IntelliJ Support

Open the project directory in IntelliJ in order to develop, run, and debug your code using an IDE.

## Maven Support

You can use the following commands to build, test, package, and run your code.

| Command                    | Description                                     |
| -------------------------- | ----------------------------------------------- |
| `mvn compile`              | Builds the code                                 |
| `mvn package`              | Run the tests and build an Uber jar file        |
| `mvn package -DskipTests`  | Build an Uber jar file                          |
| `mvn install`              | Installs the packages into the local repository |
| `mvn test`                 | Run all the tests                               |
| `mvn -pl shared test`      | Run all the shared tests                        |
| `mvn -pl client exec:java` | Build and run the client `Main`                 |
| `mvn -pl server exec:java` | Build and run the server `Main`                 |

These commands are configured by the `pom.xml` (Project Object Model) files. There is a POM file in the root of the project, and one in each of the modules. The root POM defines any global dependencies and references the module POM files.

## Running the program using Java

Once you have compiled your project into an uber jar, you can execute it with the following command.

```sh
java -jar client/target/client-jar-with-dependencies.jar

♕ 240 Chess Client: chess.ChessPiece@7852e922
```

https://sequencediagram.org/index.html?presentationMode=readOnly#initialData=IYYwLg9gTgBAwgGwJYFMB2YBQAHYUxIhK4YwDKKUAbpTngUSWDABLBoAmCtu+hx7ZhWqEUdPo0EwAIsDDAAgiBAoAzqswc5wAEbBVKGBx2ZM6MFACeq3ETQBzGAAYAdAE5M9qBACu2AMQALADMABwATG4gMP7I9gAWYDoIPoYASij2SKoWckgQaJiIqKQAtAB85JQ0UABcMADaAAoA8mQAKgC6MAD0PgZQADpoAN4ARP2UaMAAtihjtWMwYwA0y7jqAO7QHAtLq8soM8BICHvLAL6YwjUwFazsXJT145NQ03PnB2MbqttQu0WyzWYyOJzOQLGVzYnG4sHuN1E9SgmWyYEoAAoMlkcpQMgBHVI5ACU12qojulVk8iUKnU9XsKDAAFUBhi3h8UKTqYplGpVJSjDpagAxJCcGCsyg8mA6SwwDmzMSYHQo4AAa0lAxgmyQYHiCoGnJgwAQao48pQAA80RoebT+XcEeSVPUpVAeWSRConZUbs8YAozShgBb2hr0ABRK0qbAEApe26le7Fcz1QJOYLDcZzdTARkLZaRqDeOqGqZKk3B0Py+Tq9BQsycUz2vnqX1Vb0oepoHwIBCJin3Vt01S1EBq9Hu9kDHnc7QO9v3Yy1BQcDha6XaQc+4cLttjich9EKHz6jHAM-xOeYEeO5fCtcb0-6z2I3f3GFPMvYtF4tR9lgX5wh2-plq8RpKks9T7CCl76u0ED1mg0HLJciaUB2qYYPU4ROE42YTJBnwwDBwLLPB8SIchqH7Fc6AcKYXi+AE0DsIyMQinAkbSHACgwAAMhAWSFNhzDOtQAbNG0XS9AY6j5Gg2aKnMay-P8HBXGBgrAc8EEVp8ILqTsja6fCfout2CDCeKGJCSJBJEmApLvoYe40getSMiybIqVyt77qOgormKErujKmw9OW7xKgFHlBcmFldrU4XbiqaqagAkmgVCmkgG5+TA0AwMZAI7m5Ek1Cl0xXtASAAF4oBw0axvGhTaYl8DIGmGYAIyEbmqj5vMizFqW9Q+DV+p1Y1uz0c25WCq5tQ1EgABm8qlYxrmCne9JHnIKAvvEF5Xjee0Cg+q7roGZ3bjtnVmbU9nihkqiAZgZmgdUelEQZI2wWMlHUQ2kJaT98Ipt1OF4QRox-TFnyQisQNXiDKFg02jGeN4fj+F4KDoDEcSJATRP2b4WBiUtEO1A00iRgJkbtJG3Q9PJqiKcMwNIegGHmQ8sLPDzyGfY8IGVUi1n2JTp0IbzaAuZZu2BfyXlMsdctUQr87xfelQheKz53fIOpRZAosXd9yXHZ66UhllOV5RuxUzNknMOCaaMK4tnVgdVlEzU1LUoHGin81h0NgLUfUDfyw17GN0ATVN8RB3NWOmA9VKq-SHAoNwJ5Xlr6O67yCUG8KGQzBANC3a+93K494vPBTZ5vR9X1+7TIzg5JkOVGJtSw9m83Y8xeMohu-jYOKmoCWiMAAOJKho1OVc8DRL8zbP2Eq3Pe6LHWVE9It813SVUFLaIr7mJc677Od6-S3ma2fitxeX+tCqKRv19e24rbdxtibYAphVQOxgNlXKyANzv19hvOozJU7pxDmHBMHUoYlGjrHeGg0E6jRLMnBUKCoANSao2BiWcm5Py-vSZAORb5qAxGXRcl1K61AyBYVAddTQIGXkqT0QDJaui3oI7QLhJGdAQSfFudQF6MNXh3BAQE5HWyquMPeuYFgNEkS4TofckxYLTCPeGWi1A6L0QYzOOMWL+A4AAdjcE4FATgYiRmCHAbiAA2eAk5DBMJgEUKONN+501aB0Xe+9U7o2zOYgAckqQxmFPxyNqO-NYCTYoX07FfV0B10RMIxHAfxTDHJqGco-GQucxyv2Lu-VhB5grClCsbBu8hP5sPUUiW2aUIEaigU7WBXt5ZHyboggOtUyGzTQW1COnUh64JzPHAshDxokMDtMihY9qFdhVs-Q8pSlQYnMedGpzTajZQGMwJhQjznALyd2cxmVpAyMFt+WoJTjwoDKQBFRYshYD1yb9Z50gFiguSUCoepjNFKheYWCFNiJ4BEsAXaymxiZIASGAVF-YIAYoAFIQHFAIuYMRkigHVME7BoSqqNCaMyWSPRzEH1GegbM2AEDAFRVAOAEBrJQEyXC6QkKdJpIySVLlPK+UCqFXMF5ALvy0qRAAK2JWgIpRLxS-MJBUpWez3J0NqRreph90CNIrj-Vp-87kHO6a6XpHT7YDOgc7EZ2sxkGomcgzZ5DmoxlDnMzBg8o4xycP1PBKyAZJzLJNX1s1KELWztUg56swBFNBRa7+hsJS3MAfckR3Y81Ov6ZqQJHAIBqBgGgCAzBrRojef7AAQqGcpORZnh2DV1bBYa4bLLzKssYMb6h6A3CiXVORE3Y2TctVaG0YD6jkDAEA-LirZBgDLCA2NS3wFXbAU05pawRnauMy+zwgyHvDMhDtGCIaRx7RmLMkaB3RqIWWFdAqqyHoXceqduzHn7KNbUPwWhCnHNOdoLNS4OHMmwKBgJ4iOkPVSYC2oWqNVKmUaowF6i9KioWaGmFOzbF4y8NyzF2KyPykQCGfd2BOWEDyAUIJ68z11HpozZmrNejGHmbI1DGIa2yi3ZYUkOTlogG4HgFhVSLrjik1Ad0qgZNAI4dXWuhg+Gbg9I3A1tC2Hydo0w5TUH2E-3U7w-spKUBvhoSmoDknaOa1MxcizmmrOOrAch-jHyaN4Cw4qiWEze7zOMTDfCo9M5AA
