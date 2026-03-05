Module : [[DBMS Module 3]]


### Definition

A **Minimal Cover** (also called **Canonical Cover**) is the **simplified set of functional dependencies** that is **equivalent to the original set**, but contains **no redundant dependencies or attributes**.

In simple terms:  
Minimal cover is the **smallest possible set of functional dependencies that produces the same result as the original set**.

---

## Conditions of Minimal Cover

A set of functional dependencies is a **minimal cover** if it satisfies these conditions:

1. **Each functional dependency has only one attribute on the right-hand side.**
2. **No extraneous attributes exist on the left-hand side.**
3. **No redundant functional dependencies exist.**

---

# Steps to Find Minimal Cover

### Step 1: Make RHS Single Attribute

Split functional dependencies so that **each dependency has only one attribute on the right side**.

Example

Original FD:

```
A → BC
```

Convert to:

```
A → B  
A → C
```

---

### Step 2: Remove Extraneous Attributes

Check if any attribute on the **left side is unnecessary**.

Example

```
AB → C
```

If **A alone determines C**, then **B is extraneous**.

So it becomes:

```
A → C
```

---

### Step 3: Remove Redundant Dependencies

Check if any dependency can be **derived from others**.

Example

```
A → B  
B → C  
A → C
```

Here **A → C** is redundant because it can be derived from:

```
A → B  
B → C
```

So we remove:

```
A → C
```

---

# Example

Given FDs:

A → BC  
B → C  
A → B  
AB → C

### Step 1: Split RHS

A → B  
A → C  
B → C  
AB → C

### Step 2: Remove extraneous attributes

`AB → C` becomes redundant because **B → C** already exists.

### Final Minimal Cover

A → B  
A → C  
B → C

---

# Importance of Minimal Cover

Minimal cover is used for:

- **Database normalization**
    
- **Removing redundant functional dependencies**
    
- **Designing efficient database schemas**