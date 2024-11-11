# Analisando a parte 3 da prática de orientação a objetos  
## João Antonio B. Lobler
## Sistemas de Informação

### Análise do diagrama de classes:
![image](https://github.com/user-attachments/assets/5d309f41-897d-426b-a72f-e339c38a2116)

Analisando rapidamente é possível perceber que o diagrama nos apresenta um sistema definido em 3 classes com atributos e métodos definidos, sendo elas as classes de:
* Student
* Professor
* Group
  
Sendo a última classe citada a que se relaciona com as 2 primeiras como indicado pelo "has-a"

### Completando o código

O exercício pedia que fosse completado dois métodos que estavam definidos na classe `group`

Primeramente o método `userExists` 
~~~
public boolean userExists(String userId) {
    // COMPLETE-ME
    // Verifique se existe o userId na lista de estudantes ou de professores
    // Veja no método anterior como percorrer as listas de estudantes e professores

  }
~~~

E seguidamente o método `countMembers`
~~~
public int countMembers() {
    // COMPLETE-ME
    // Retorne o total de membros do grupo (estudantes e professores)
    // Para isso, descubra qual método chamar para obter o tamanho de um ArrayList
  }
~~~

Completando primeiramente o método `userExists`, implementar ele foi bem simples:

~~~
public boolean userExists(String userId) {

        for (Student student : students) {
            if (student.getUserId().equals(userId)) {
                return true;
            }
        }

        for (Professor professor : professors) {
            if (professor.getUserId().equals(userId)) {
                return true;
            }
        }
        
        return false;

    }
~~~

Um método que foi implementado da seguinte forma ele percorre a lista de alunos ou de professores e então em cada uma das iterações ele verifica a condição, é chamado o método `getUserId` (que é publico) para
decobrir qual id esta relacionado à aquele estudante/professor e o `equals` faz como que ele seja comparado com o `userId` passado como paramêtro, caso seja verdadeiro retorna `true` caso não esteja na lista retorna `false`.

Para implementar o método countMembers não foi complicado também, o método `.size` retorna o tamanho de um array em java dessa forma como o método serve para retornar a quantidade total de pessoas no grupo o código fica dessa forma:

~~~
public int countMembers() {
        
        return students.size() + professors.size();
    }
~~~

![image](https://github.com/user-attachments/assets/490afaba-8ea2-4e56-847c-45c2dba19c7a)

Desse modo quando o Main é rodado, é feita a instância das 3 classes e também feita a chamada dos métodos, trazendo assim então a saída que o exercício dava como correta.

## Refletindo sobre o código:

### Você consegue identificar alguma redundância nos códigos (dentro de uma mesma classe ou em classes diferentes)?

Na minha análise eu destaquei que é possível perceber que seria possível existir uma superclasse `pessoa` e que as classes professor e estudante herdassem ela, afinal existem atributos que ambos possuem como `name` e `UserId` e seus respectivos Getters e Setters que se repetem desnecessariamente.

### O que aconteceria se fosse necessário armazenar outros atributos sobre estudantes e professores? (por exemplo, CPF, data de nascimento, telefone, etc?)

Supondo que tanto professor quanto estudante receberiam esses atributos, o código ficaria ainda mais redundante, a solução para tal caso ao meu ver seria implementar uma superclasse `pessoa` que já tivesse esses atributos e seus respectivos métodos getter e setter.

### O que aconteceria na classe Group se tivéssemos outras categorias de membros além de estudantes e professores (técnicos, administradores, etc.)?

Se a classe Group fosse expandida para incluir outras categorias de membros como técnicos e administradores, haveria um aumento da complexidade no código. Atualmente, `Group` possui métodos específicos para adicionar `Student` e `Professor` `(addMember(Student s) e addMember(Professor p))`, e mantém listas separadas para cada tipo de membro. Isso não escalaria bem com mais categorias de membros, e resultaria em código mais difícil de manter, com maior redundância e complexidade, afinal teriam de ser criados cada vez mais métodos com a mesma função.




### Referências:

* https://www.dio.me/articles/o-uso-do-arraylist-em-java
* https://www.dio.me/articles/equals-em-java-compreendendo-e-implementando-a-comparacao-de-objetos


