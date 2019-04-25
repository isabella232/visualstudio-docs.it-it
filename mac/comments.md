---
title: Codice di impostazione come commento
description: Questo articolo descrive l'uso dei commenti nell'editor standard di Visual Studio per Mac
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 1f792e5ba670854e4a3a9ce703212d18c16e5512
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62984028"
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

## <a name="see-also"></a>Vedere anche

- [Codice di impostazione come commento (Visual Studio in Windows)](/visualstudio/ide/quickstart-editor#comment-out-code)