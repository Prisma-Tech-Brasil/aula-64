
# **Interfaces vs Types no TypeScript**

Quando você começa a trabalhar com TypeScript, uma dúvida comum surge: **Devo usar `interface` ou `type`?** Ambos são usados para definir a forma de objetos, mas têm algumas diferenças importantes. Vamos entender como cada um funciona e quando usar cada um.

---

## **1. O que é uma Interface?**

Uma **interface** é uma forma de definir a estrutura de um objeto. É muito usada para descrever a forma de classes ou objetos complexos. Interfaces são **extensíveis**, o que significa que você pode adicionar propriedades a elas depois.

### **Exemplo de Interface:**

```typescript
interface User {
  name: string;
  age: number;
  isAdmin?: boolean; // Propriedade opcional
}

const user1: User = {
  name: "João",
  age: 25,
};
```

### **Extensão de Interfaces:**

Interfaces podem ser **extendidas** para criar novas interfaces.

```typescript
interface Admin extends User {
  permissions: string[];
}

const admin1: Admin = {
  name: "Maria",
  age: 30,
  permissions: ["read", "write", "delete"],
};
```

---

## **2. O que é um Type?**

O **type** também define a estrutura de um objeto, mas é mais **flexível**. Além de objetos, você pode criar **tipos primitivos**, **uniões** e **interseções**.

### **Exemplo de Type:**

```typescript
type User = {
  name: string;
  age: number;
  isAdmin?: boolean;
};

const user2: User = {
  name: "Carlos",
  age: 28,
};
```

### **União de Tipos:**

Você pode criar tipos que aceitam múltiplos formatos usando `|` (pipe).

```typescript
type ID = string | number;

const userId: ID = "123ABC";
const anotherId: ID = 456;
```

### **Interseção de Tipos:**

Combina múltiplos tipos em um só usando `&`.

```typescript
type Address = {
  street: string;
  city: string;
};

type UserWithAddress = User & Address;

const user3: UserWithAddress = {
  name: "Ana",
  age: 22,
  street: "Rua das Flores",
  city: "Vitória",
};
```

---

## **3. Qual a Diferença Entre Interface e Type?**

| Característica              | **Interface**                              | **Type**                                |
|-----------------------------|--------------------------------------------|-----------------------------------------|
| Extensão                    | Pode ser estendida com `extends`           | Usa interseção `&` para combinar tipos  |
| Unir Tipos                  | Não suporta uniões diretamente             | Suporta uniões com `|`                  |
| Merging (Mesclagem)         | Permite declaração múltipla (mescla automática) | Não permite mesclagem                   |
| Usabilidade                 | Preferida para **classes** e **OOP**       | Flexível para **tipos primitivos** e **uniões** |
| Performance                 | Interfaces podem ter uma leve vantagem de performance em projetos grandes | Pouca diferença perceptível             |

---

## **4. Quando Usar Interface ou Type?**

- **Use `interface`** quando:
  - Está lidando com **classes** ou **herança**.
  - Precisa de algo que pode ser **expandido** ou **extendido**.
  - Está criando **bibliotecas públicas** (facilita a extensão por outros devs).

- **Use `type`** quando:
  - Precisa de **tipos complexos**, como **uniões** e **interseções**.
  - Quer definir **alias** para tipos primitivos (`string`, `number`, etc.).
  - Está lidando com **tipos literais** ou **tuplas**.

---

## **5. Conclusão**

No final das contas, tanto `interface` quanto `type` são ferramentas poderosas do TypeScript. A escolha entre eles depende do contexto do seu projeto. Se você precisar de algo simples e extensível, vá de **interface**. Se precisar de algo mais flexível e complexo, escolha o **type**.

---

## **Referências**

- [Documentação Oficial do TypeScript - Interfaces](https://www.typescriptlang.org/docs/handbook/interfaces.html)
- [Documentação Oficial do TypeScript - Type Aliases](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#type-aliases)

---

Se precisar de mais exemplos ou detalhes sobre um caso específico, me avisa! 😊
