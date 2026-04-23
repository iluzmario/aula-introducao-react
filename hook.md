# Hooks: useState e useEffect

Hooks são funções especiais do React que permitem usar recursos like estado e ciclos de vida em componentes funcionais.

---

## useState

O `useState` permite criar variáveis que o React consegue "monitorar" e atualizar a interface quando mudam.

### Exemplo Simples: Contador

```jsx
import { useState } from 'react';

function Contador() {
  const [numero, setNumero] = useState(0);

  return (
    <div>
      <p>Valor: {numero}</p>
      <button onClick={() => setNumero(numero + 1)}>Aumentar</button>
    </div>
  );
}
```

**O que acontece:**
- `useState(0)` cria uma variável chamada `numero` com valor inicial `0`
- `setNumero` é a função para alterar o valor
- Quando `numero` muda, o componente re-renderiza automaticamente

---

## useEffect

O `useEffect` executa código quando o componente é exibido ou quando algo muda.

### Exemplo 1: Executar ao abrir a página

```jsx
import { useEffect } from 'react';

function Saudacao() {
  useEffect(() => {
    console.log('Componente carregou!');
  }, []); // colchetes vazios = executa só uma vez

  return <h1>Olá!</h1>;
}
```

### Exemplo 2: Executar quando algo muda

```jsx
import { useState, useEffect } from 'react';

function Nome() {
  const [nome, setNome] = useState('Maria');

  useEffect(() => {
    console.log('O nome mudou para:', nome);
  }, [nome]); // executa quando 'nome' mudar

  return (
    <div>
      <p>{nome}</p>
      <button onClick={() => setNome('João')}>Mudar Nome</button>
    </div>
  );
}
```

---

## Resumo Rápido

| Hook | Para que serve |
|------|----------------|
| `useState` | Guardar e atualizar valores (como uma variável especial) |
| `useEffect` | Fazer algo quando algo mudar (como carregar dados) |

---

## Dica

- Use `useState` quando precisar de dados que mudam na tela
- Use `useEffect` quando precisar buscar dados, conectar eventos, ou fazer algo "colateral"