---
title: Annotazioni di struct e classi
ms.date: 06/28/2019
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
- _Field_z_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 35be465064c9524eb0e1339794b6a19b7a595da1
ms.sourcegitcommit: d2b234e0a4a875c3cba09321cdf246842670d872
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2019
ms.locfileid: "67493640"
---
# <a name="annotating-structs-and-classes"></a>Annotazioni di struct e classi

È possibile annotare i membri struct e di classe utilizzando le annotazioni che operano come invarianti, si presume che siano true per qualsiasi chiamata di funzione o entrata/uscita di funzione che include la struttura contenitore come parametro o valore restituito.

## <a name="struct-and-class-annotations"></a>Annotazioni di classi e struct

- `_Field_range_(low, high)`

     Il campo è compreso nell'intervallo (inclusivo) dal `low` a `high`.  Equivalente ad applicare `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` all'oggetto annotato utilizzando le pre/postcondizioni appropriate.

- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     Campo con una dimensione scrivibile in elementi (o byte) come specificato da `size`.

- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`

     Campo con una dimensione scrivibile in elementi (o byte) come specificato da `size` e `count` degli elementi (byte) che sono leggibili.

- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     Campo che contiene sia dimensione leggibile che modificabile in elementi (o byte) come specificato da `size`.

- `_Field_z_`

     Un campo contenente una stringa con terminazione null.

- `_Struct_size_bytes_(size)`

     Si applica alla dichiarazione di classe o struct.  Indica che un oggetto valido di tale tipo può essere maggiore rispetto al tipo dichiarato, con il numero di byte specificati da `size`.  Ad esempio:

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     Le dimensioni del buffer in byte di un parametro `pM` di tipo `MyStruct *` viene quindi considerato:

    ```cpp
    min(pM->nSize, sizeof(MyStruct))
    ```

## <a name="example"></a>Esempio

```cpp
#include <sal.h>
// For FIELD_OFFSET macro
#include <windows.h>

// This _Struct_size_bytes_ is equivalent to what below _Field_size_ means.
_Struct_size_bytes_(FIELD_OFFSET(MyBuffer, buffer) + bufferSize * sizeof(int))
struct MyBuffer
{
    static int MaxBufferSize;
    
    _Field_z_
    const char* name;
    
    int firstField;

    // ... other fields

    _Field_range_(1, MaxBufferSize)
    int bufferSize;
    _Field_size_(bufferSize)        // Prefered way - easier to read and maintain.
    int buffer[0];
};
```

Note per questo esempio:

- `_Field_z_` è equivalente a `_Null_terminated_`.  `_Field_z_` per il nome del campo specifica che il campo nome è una stringa con terminazione null.
- `_Field_range_` per la `bufferSize` specifica che il valore di `bufferSize` deve essere compresa tra 1 e `MaxBufferSize` (entrambi compresi).
- I risultati finali del `_Struct_size_bytes_` e `_Field_size_` le annotazioni sono equivalenti. Per le strutture o classi che dispongono di un layout simile `_Field_size_` è più facile da leggere e gestire, perché contiene un numero inferiore calcoli maggiore rispetto all'equivalente e riferimenti `_Struct_size_bytes_` annotazione. `_Field_size_` non richiede la conversione per le dimensioni in byte. Se la dimensione in byte è l'unica opzione disponibile, ad esempio, per un campo del puntatore void, `_Field_size_bytes_` può essere utilizzato. Se entrambe `_Struct_size_bytes_` e `_Field_size_` esiste, entrambi saranno disponibili per gli strumenti. È compito lo strumento cosa fare se le due annotazioni non sono d'accordo.

## <a name="see-also"></a>Vedere anche

- [Uso delle annotazioni SAL per ridurre gli errori del codice C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Informazioni su SAL](../code-quality/understanding-sal.md)
- [Annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md)
- [Annotazione del comportamento delle funzioni](../code-quality/annotating-function-behavior.md)
- [Annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md)
- [Specificare dove e quando applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funzioni intrinseche](../code-quality/intrinsic-functions.md)
- [Suggerimenti ed esempi](../code-quality/best-practices-and-examples-sal.md)