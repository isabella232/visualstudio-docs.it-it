---
title: Aggiungere un parametro a un'azione rapida per un metodo
description: Informazioni su come usare un'azione rapida per aggiungere e dichiarare automaticamente un parametro, in base all'utilizzo, a un metodo.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: c48e062ec4187fad479f5013fb8786c7eb018cc2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123970"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Aggiungere un parametro a un metodo tramite un'azione rapida

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Che cosa:** permette di aggiungere automaticamente un parametro a un metodo, in base all'utilizzo.

**Quando:** si vuole aggiungere un parametro a un metodo e dichiararlo nel modo corretto automaticamente.

**Perché:** sarebbe anche possibile aggiungere il parametro alla dichiarazione del metodo prima di chiamarlo, ma questa funzionalità lo aggiunge automaticamente in base una chiamata del metodo.

## <a name="how-to-use-it"></a>Modo d'uso

1. Aggiungere un argomento aggiuntivo a una chiamata del metodo.

   Sotto il nome del metodo in cui viene chiamato viene visualizzata una linea a linee rossa.

2. Posizionare il puntatore del mouse sulla linea a forma di ondro rossa fino a quando non viene visualizzato il menu Azioni rapide. Selezionare la **freccia verso il basso** nel menu Azioni rapide e quindi selezionare **Aggiungi il parametro a [metodo]**.

   ![Azione rapida di aggiunta del parametro al metodo in Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > È anche possibile accedere al menu Azioni rapide posizionando il cursore sulla riga della chiamata al metodo e quindi premendo + **CTRL.** (punto) o selezionando l'icona a forma di lampadina nel margine del file.

   Visual Studio aggiunge il nuovo parametro alla dichiarazione del metodo.

> [!NOTE]
> Se vi sono altre chiamate al metodo, queste possono generare errori dopo che si usa questa azione rapida, perché non specificano un argomento per il nuovo parametro aggiunto.

## <a name="see-also"></a>Vedi anche

- [Aggiungere un parametro a un costruttore](generate-constructor.md#addparameter)
