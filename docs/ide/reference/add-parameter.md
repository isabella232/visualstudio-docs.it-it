---
title: Aggiungere un parametro a un'azione rapida per un metodo
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7de4c4aec07a3151332c199749bef4409966b3e1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929887"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Aggiungere un parametro a un metodo tramite un'azione rapida

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** permette di aggiungere automaticamente un parametro a un metodo, in base all'utilizzo.

**Quando:** si vuole aggiungere un parametro a un metodo e dichiararlo nel modo corretto automaticamente.

**Perché?:** sarebbe anche possibile aggiungere il parametro alla dichiarazione del metodo prima di chiamarlo, ma questa funzionalità lo aggiunge automaticamente in base una chiamata del metodo.

## <a name="how-to-use-it"></a>Come usare la funzionalità

1. Aggiungere un argomento aggiuntivo a una chiamata del metodo.

   Sotto il nome del metodo, nella posizione in cui viene chiamato, appare una riga rossa "ondulata".

2. Posizionare il puntatore del mouse sulla riga rossa "ondulata" fino a quando non viene visualizzato il menu Azioni rapide. Selezionare la **freccia verso il basso** nel menu Azioni rapide e quindi selezionare **Aggiungi il parametro a [metodo]**.

   ![Azione rapida di aggiunta del parametro al metodo in Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > È anche possibile accedere al menu Azioni rapide posizionando il cursore sulla riga della chiamata del metodo e quindi premendo **CTRL**+**.** oppure selezionando l'icona di lampadina nel margine del file.

   Visual Studio aggiunge il nuovo parametro alla dichiarazione del metodo.

> [!NOTE]
> Se vi sono altre chiamate al metodo, queste possono generare errori dopo che si usa questa azione rapida, perché non specificano un argomento per il nuovo parametro aggiunto.

## <a name="see-also"></a>Vedere anche

- [Aggiungere un parametro a un costruttore](generate-constructor.md#addparameter)