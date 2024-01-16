# Conteúdo básico sobre listas com Jetpack Compose

O primeiro passo é criar uma função @Composable para ser a parte visual do item da sua lista. Essa função deve receber o tipo de objeto correspondente ao seu item, por exemplo, numa lista de filmes você enviaria o objeto Filme. Nesse exemplo, vamos simular uma lista de usuários, mas pra simplificar ao invés de criar um objeto Usuário, vamos enviar apenas uma String que representa o nome do usuário.

```kotlin
@Composable
fun User(name: String) {
    Text(text = name)
}
```

Feito isso, criamos uma segunda função @Composable que será a nossa lista. De forma simples, ela vai receber uma lista de Strings com nomes de usuários, no caso do exemplo do filme receberia uma lista de Filmes e assim por diante de acordo com o tipo de lista que você precisa.

Dentro da LazyColumn teremos a propriedade items, que recebe a lista e com uma espécie de laço de repetição monta a lista criando uma instância da função que que criamos anteriormente para cada item da lista.

```kotlin
@Composable
fun UserList(userList: List<String>) {
    LazyColumn {
        items(userList) { item ->//Na LazyColumn existem pelo menos 3 tipos de implementação de items, escolha a função que recebe listas (essa List<T>).
            User(name = item)
        }
    }
}
```

Por último, crie uma lista com o tipo de objeto que deseja listar, no nosso caso uma lista de Strings. Em seguida, chame a função de lista que criamos no passo anterior passando essa lista como parâmetro.

```kotlin
val users = listOf("Mateus", "Marcos", "Lucas", "João")

UserList(users)
```

Pronto! Agora você já pode trabalhar com listas em aplicativos Android com jetpack Compose.

Se quiser ver um pouco mais, assista ao tutorial: https://youtu.be/EvdmoxOZPAI

## Listas horizontais

Se precisar trabalhar com listas horizontais, basta fazer o mesmo processo trocando o LazyColumn pelo LazyRow, como no exemplo abaixo:

```kotlin
@Composable
fun UserList(userList: List<String>) {
    LazyRow {
        items(userList) { item ->//Na LazyColumn existem pelo menos 3 tipos de implementação de items, escolha a função que recebe listas (essa List<T>).
            User(name = item)
        }
    }
}
```

Tutorial com listas horizontais: https://youtu.be/h1D_Xo6h64Q
