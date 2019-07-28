## Clean the master branch

### 1 Dentro del branch master

```
git checkout master
```

### 2 Crear un branch huerfano

```
git checkout --orphan temp_branch
```

### 3 Eliminar los archivos

```
rm -rf .*
```

### 4 Crear el archivo index.html

con el siguiente contenido

```
<!DOCTYPE html>
```

### 5 Agregar el archivo

```
git add index.html
```

### 6 Commit el archivo

```
git commit -m "Primer commit"
```

