# Padrão Composite - Instituição

## 1. Introdução

Este documento descreve a implementação do padrão de projeto **Composite** para representar a estrutura hierárquica de instituições de ensino no sistema **DicasDeEstagio**.  
O **Composite** é um padrão estrutural que permite compor objetos em estruturas de árvore para representar hierarquias parte-todo.

---

## 2. Objetivo

O padrão **Composite** foi escolhido para Instituições devido à:

- **Hierarquia natural:** Instituição → Departamento/Faculdade → Curso  
- **Tratamento uniforme:** Operações aplicáveis a toda hierarquia  
- **Flexibilidade:** Facilita adicionar novos níveis hierárquicos

---

## 3. Estrutura do Padrão

### 3.1 Diagrama de Classes

```mermaid
classDiagram
    class ComponenteInstituicional {
        <<interface>>
        +get_nome()*
        +get_descricao()*
        +exibir(nivel)*
        +adicionar(componente)*
        +remover(componente)*
        +obter_filhos()*
    }
    
    class Instituicao {
        +id: int
        +nome: str
        +sigla: str
        +tipo: str
        +endereco: str
        +site: str
        +filhos: List
        +get_nome()
        +adicionar()
        +remover()
        +exibir()
    }
    
    class Departamento {
        +id: int
        +nome: str
        +codigo: str
        +instituicao: FK
        +pai: FK
        +filhos: List
        +get_nome()
        +adicionar()
        +remover()
        +exibir()
    }
    
    class Curso {
        +id: int
        +nome: str
        +codigo: str
        +departamento: FK
        +duracao: int
        +get_nome()
        +exibir()
    }
    
    ComponenteInstituicional <|.. Instituicao
    ComponenteInstituicional <|.. Departamento
    ComponenteInstituicional <|.. Curso
    Instituicao "1" --> "*" Departamento
    Departamento "1" --> "*" Curso
    Departamento "1" --> "*" Departamento : subdepartamentos
```

---

## 4. Implementação em Django

### 4.1 Models (models.py)

```python
# (Conteúdo do código models.py conforme o documento original)
```
---

### 4.2 Serializers (serializers.py)

```python
# (Conteúdo do código serializers.py conforme o documento original)
```
---

### 4.3 Views (views.py)

```python
# (Conteúdo do código views.py conforme o documento original)
```
---

## 5. Exemplo de Uso

### 5.1 Construindo a Hierarquia

```python
from .models import Instituicao, Departamento, Curso

# Criar instituição (raiz)
unb = Instituicao.objects.create(
    nome='Universidade de Brasília',
    sigla='UnB',
    tipo='universidade_publica'
)

# Criar departamento
fga = Departamento.objects.create(
    nome='Faculdade do Gama',
    codigo='FGA',
    instituicao=unb
)

# Adicionar departamento usando Composite
unb.adicionar(fga)

# Criar curso
eng_soft = Curso.objects.create(
    nome='Engenharia de Software',
    codigo='ES',
    departamento=fga,
    nivel='graduacao',
    duracao=10
)

# Adicionar curso usando Composite
fga.adicionar(eng_soft)

# Exibir hierarquia
print(unb.exibir())
```

---

## 6. Vantagens da Implementação

- ✅ **Uniformidade:** Trata objetos individuais e composições de forma uniforme  
- ✅ **Recursividade:** Operações funcionam recursivamente na hierarquia  
- ✅ **Flexibilidade:** Fácil adicionar novos níveis hierárquicos  
- ✅ **Manutenibilidade:** Estrutura clara e organizada  
- ✅ **Navegação:** Facilita navegação na árvore de componentes

---

## 7. Testes

```python
# (Conteúdo dos testes conforme o documento original)
```

---

## 8. Referências

- Gamma, E. et al. (1994). *Design Patterns: Elements of Reusable Object-Oriented Software*  
- Django Documentation: https://docs.djangoproject.com/  
- Django REST Framework: https://www.django-rest-framework.org/

---

**Histórico de Versões**

| Versão | Data | Descrição | Autor |
|--------|------|-----------|-------|
| 1.0 | 24/10/2025 | Criação do documento | Equipe G5 |
