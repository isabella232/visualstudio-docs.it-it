---
title: Aggiungere controlli Null per tutti i parametri
ms.date: 07/24/2019
ms.topic: reference
author: stcahlon
ms.author: t-shzach
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: da3a616844dbe914cfe796ec35d1501bf83dd1ef
ms.sourcegitcommit: 3e74ec49a54e5c3da7631f4466128cdf4384af6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/01/2019
ms.locfileid: "68712733"
---
# <a name="add-null-checks-for-all-parameters"></a>Aggiungere controlli null per tutti i parametri 

Questo refactoring si applica a: 

- C# 

**Cosa:** crea e aggiunge istruzioni `if` che controllano la presenza di valori Null in tutti i parametri Nullable non controllati. 

**Quando:** si vogliono aggiungere rapidamente controlli Null per tutti i parametri del metodo applicabili.

**Perché?:** la scrittura di controlli Null per molti parametri può essere un'operazione lunga e ripetitiva. L'uso di questo refactoring è rapido e rende il programma più stabile.  

## <a name="how-to"></a>Procedura 

1. Posizionare il cursore su qualsiasi parametro all'interno del metodo.

2. Premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring**.

   ![Azioni rapide e refactoring](media/add-null-checks-for-all-parameters.png)
   
3. Selezionare l'opzione per **aggiungere controlli Null per tutti i parametri**.

   ![Aggiungere controlli Null per tutti i parametri](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Vedere anche 

- [Refactoring](../refactoring-in-visual-studio.md) 
