Um array ou lista são conjuntos de dados colocados adjacentes, ou seja, um depois do outro. Eles podem ser acessados através da sua posição, que começa no 0 e vai até n - 1, onde n é o número de elementos. Além disso, todos os dados são necessariamente do mesmo tipo. Por fim, cada array conterá um tamanho que será dito como `length`. Por padrão, o último indíce é `length - 1`.

Essa estrutura de dados é bem básica e nos permite realizar várias operações de maneira simples.

```
namespace Linear;

public class List<T>
{
    private int realsize = 10;
    private T[] arr;
    private int _length = 0;
    public int Length {get => _length;}
    public T[] ToArray {get => (T[]) arr.Clone();}
    public List() {
        arr = new T[realsize];
    }
    public bool Contains(T value) {
        for(int i = 0; i < Length; i++) {
            T e = arr[i];
            if(e == null) {
                continue;
            }
            if(e.Equals(value)) {
                return true;
            }
        }
        return false;
    }
    public T this[int i] 
    {
        get {return arr[i];}    
    }
    /**
        Duplicate the old array into a new bigger one.
        O(n) where n is the size of the original array.
    */
    private void realloc() {
        realsize = Length + (Length / 4);
        T[] narr = new T[realsize];
        for(int i = 0; i < Length; i++) {
            narr[i] = arr[i];
        }
        arr = narr;
    }
    private bool needRealloc() {
        return Length >= realsize;
    }
    /**
        Insert a given value into the end of the array.
        The operation itself O(1), but I can be turned into a O(n) since reallocation is needed sometimes.
    **/
    public void Append(T value) {
        if(needRealloc()) {
            realloc();
        }
        arr[_length++] = value;
    }
    /**
        Insert a given value into the beggining of the array.
        O(n) since it needs to move all the elements inside the array to the right.
    **/
    public void Unshfit(T value) {
        if(needRealloc()) {
            realloc();
        }
        for(int i = Length - 1; i >=0; i--) {
            arr[i + 1] = arr[i];
        }
        arr[0] = value;
        _length++;
    }
    /**
        Insert a given value into POSITION of the array.
        O(n) since it needs to move all the elements inside the array to the right.
    **/
    public void InsertAt(T value, int position) {
        if(needRealloc()) {
            realloc();
        }
        if(position < 0 || position > Length) {
            throw new IndexOutOfRangeException($"position must be a value between 0 and {Length}");
        }
        if(position == Length) {
            Append(value);
            return;
        }
        if(position == 0) {
            Unshfit(value);
            return;
        }        
        for(int i = Length - 1; i >= position; i--) {
            arr[i + 1] = arr[i];
        }
        arr[position] = value;
        _length++;
    }
    /**
        Remove an element from the end of the array.
        O(1)
    */
    public T Pop() {
        var item = arr[Length - 1];
        arr[Length - 1] = default;
        _length--;
        return item;
    }
    /**
        Remove an element from POSITION of the array.
        O(n)
    */
    public T RemoveAt(int position) {
        if(position < 0 || position > Length) {
            throw new IndexOutOfRangeException($"position must be a value between 0 and {Length}");
        }
        if(position == (Length - 1)) {
            return Pop();
        }
        var item = arr[position];
        for(int i = position; i < (Length - 1); i++) {
            arr[i] = arr[i + 1];
        }
        _length--;
        return item;
    }
    public override string ToString()
    {
        return arr.ToString() ?? "[]";
    }
}
```

### Análise de Complexidade
Inserir ou remover em uma lista dessa sempre será `O(n)`ou `O(1)`. Nesse caso, somente teremos o `O(1)`quando fazemos operação de inserção e remoção no final da lista. Entretanto, no meio da lista, teremos sempre `O(n)`, pois é necessário mover os elementos para direita ou esquerda.