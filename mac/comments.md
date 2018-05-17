---
title: Commenti
description: Questo articolo descrive l'uso dei commenti nell'editor standard di Visual Studio per Mac
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 4a7dfd0daaddad9f91d461689a0174469dd253c2
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
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

``` cs
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
