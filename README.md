# Managing Secrets with Vault and Consul

## Want to learn how to build this?

Check out the [post](https://testdriven.io/managing-secrets-with-vault-and-consul).

## Want to use this project?

1. Fork/Clone

1. Build the images and run the containers:

    ```sh
    $ docker-compose up -d --build
    ```

1. You can now interact with both Vault and Consul. View the UIs at [http://localhost:8200/ui](http://localhost:8200/ui) and [http://localhost:8500/ui](http://localhost:8500/ui).

```
vault write secret/test heslo=abc
vault read secret/test
vault read -field=heslo secret/test
echo "export HESLO=$(vault read -field=heslo secret/test)" >> .env
source .env
echo $HESLO
unset HESLO
echo $HESLO
vault write secret/test value=@test.json
 vault read secret/test 
Key                 Value
---                 -----
refresh_interval    768h
value               { "hello" : "world" }
vault read -field=value secret/test
```
