---
title: Codice di impostazione come commento
description: Questo articolo descrive l'uso dei commenti nell'editor standard di Visual Studio per Mac
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.topic: how-to
ms.openlocfilehash: 0207c616069fdec1e0fdca0e9efcc1a7bf99a2e5dd60e6b13a24b1515be0cc6b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121407192"
---
# <a name="comments"></a>Commenti

Durante l'esecuzione del debug o di esperimenti con il codice, può essere utile impostare blocchi di codice come commenti, temporaneamente o a lungo termine.

Per impostare un intero blocco di codice come commento:

* Selezionare il codice e selezionare **Attiva/Disattiva commento per riga** dal menu di scelta rapida

OR

* Usare il tasto di scelta rapida `cmd + /` sul codice selezionato.

Questi metodi possono essere usati per impostare come commenti una o più sezioni di codice, nonché per annullare questa impostazione. Nei file C# è possibile aggiungere altri livelli di commenti riga. Ciò consente di impostare aree di codice come commenti e di annullare questa impostazione mantenendo comunque i commenti effettivi:

![Commenti a più livelli](media/source-editor-image8.png)

I commenti sono utili anche per la documentazione di codice per gli sviluppatori che potranno interagire con esso in futuro. Tali commenti vengono in genere creati sotto forma di commenti su più righe e per ogni lingua vengono aggiunti nel modo seguente:

**C#**

```csharp
/*
 This is a multi-line
 comment in C#
*/
```

**F#**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```

## <a name="see-also"></a>Vedi anche

- [Codice di impostazione come commento (Visual Studio in Windows)](/visualstudio/ide/quickstart-editor#comment-out-code)