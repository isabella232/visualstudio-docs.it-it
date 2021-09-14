---
title: Finestra di dialogo Risolvi ambiguità | Microsoft Docs
description: Esaminare Visual Studio finestra di dialogo Risolvi ambiguità, che viene visualizzata quando il debugger non è in grado di scegliere la posizione da visualizzare.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.Disambig
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c94742816f2149b53947fa3475c33b14ed7367c5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627875"
---
# <a name="resolve-ambiguity-dialog-box"></a>finestra di dialogo Risolvi ambiguità
La finestra di dialogo `Resolve Ambiguity` viene visualizzata quando il debugger non è in grado di determinare il percorso da visualizzare. Se, ad esempio, si utilizzano i modelli C++, è possibile creare più funzioni da un unico modello di funzione. Se il debugger si arresta in corrispondenza di un percorso di origine nel modello e si sceglie `Go To Disassembly`, possono verificarsi più condizioni. Ciascuna funzione creata dal modello ha un proprio codice disassembly e il debugger non è in grado di determinare quale codice si desidera visualizzare. La finestra di dialogo `Resolve Ambiguity` consente di selezionare il percorso desiderato da un elenco di tutti i percorsi corrispondenti.

 `Choose the specific location` Elenca tutti i percorsi corrispondenti al comando.

 `Address` Mostra gli indirizzi di memoria per ogni funzione.

 `Function` Mostra il nome di ogni funzione.

 `Module` Mostra il modulo (EXE o DLL) che contiene il codice oggetto per la funzione.

## <a name="see-also"></a>Vedi anche
- [Espressioni nel debugger](../debugger/expressions-in-the-debugger.md)