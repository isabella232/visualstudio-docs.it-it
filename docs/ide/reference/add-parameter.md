---
title: Aggiungere un parametro a un'azione rapida per un metodo
ms.date: 09/28/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4dbed81809cb3b69814fbf10dde7129b45396eaa
ms.sourcegitcommit: 7825d4163e52d724e59f6c0da209af5fbef673f7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2019
ms.locfileid: "72000203"
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

   Una zigzag rossa viene visualizzata sotto il nome del metodo in cui viene chiamato.

2. Posizionare il puntatore sul zigzag rosso fino a quando non viene visualizzato il menu azioni rapide. Selezionare la **freccia verso il basso** nel menu Azioni rapide e quindi selezionare **Aggiungi il parametro a [metodo]** .

   ![Azione rapida di aggiunta del parametro al metodo in Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > È anche possibile accedere al menu Azioni rapide posizionando il cursore sulla riga della chiamata del metodo e quindi premendo **CTRL**+ **.** (periodo) o selezionando l'icona a bulbo di luce nel margine del file.

   Visual Studio aggiunge il nuovo parametro alla dichiarazione del metodo.

> [!NOTE]
> Se vi sono altre chiamate al metodo, queste possono generare errori dopo che si usa questa azione rapida, perché non specificano un argomento per il nuovo parametro aggiunto.

## <a name="see-also"></a>Vedere anche

- [Aggiungere un parametro a un costruttore](generate-constructor.md#addparameter)