# Appeler un constructeur de classe de base

Pour appeler un constructeur de classe de base à partir d’une sous-classe, utilisez le mot clé **base** :

```PowerShell
class A 
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

Si une classe de base a un constructeur par défaut (sans paramètre), vous pouvez omettre un appel de constructeur explicite :

```PowerShell
class C : B
{
    C([int]$c) {}
}
```<!--HONumber=Mar16_HO2-->
