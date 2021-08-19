---
title: Installare Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: how-to
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protezione, edizione community, offuscamento, .NET, gratis, Visual Studio 2017, Visual Studio 2019, Visual Studio, installare
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: Informazioni su come installare la copia gratuita di Dotfuscator Community inclusa in Visual Studio.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 43047bfe02f510d65e7e72995af9a38f4afe8aa8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124022"
---
# <a name="install-dotfuscator-community"></a>Installare Dotfuscator Community

Dotfuscator Community è un componente facoltativo di Visual Studio.
Queste istruzioni spiegano come installarlo.

> [!NOTE]
> Oltre alle versioni di Dotfuscator Community incluse nelle versioni di Visual Studio, PreEmptive Solutions offre periodicamente anche versioni aggiornate sul proprio sito Web.
> Se si vuole scaricare la **versione più recente** direttamente anziché eseguire l'installazione da Visual Studio, **[fare clic qui per passare alla pagina di download di Dotfuscator][download]**.

## <a name="within-visual-studio"></a>Da Visual Studio

::: moniker range="vs-2019"

È possibile installare Dotfuscator Community dall'IDE di Visual Studio:

1. Nella **casella di ricerca** (CTRL+Q) digitare `dotfuscator`. <br/> <br/> ![Casella di ricerca](media/install_in_vs19_12.png) <br/> <br/>

2. Nei risultati di visualizzati, sotto l'intestazione *Componenti*, selezionare **Installa PreEmptive Protection - Dotfuscator**.
   * Se invece sotto l'intestazione *Menu* viene visualizzato **PreEmptive Protection - Dotfuscator Community** vuol dire che Dotfuscator Community è già installato. Selezionare tale opzione per [iniziare][get-started].

3. Verrà visualizzata la finestra del programma di installazione di Visual Studio, preconfigurata per installare Dotfuscator Community.
   > [!NOTE]
   > Potrebbe essere necessario specificare credenziali di amministratore per continuare.

4. Fare clic su *Installa* nella finestra del programma di installazione di Visual Studio. <br/> <br/> ![Fare clic su Installa](media/install_in_vs19_34.png) <br/> <br/>

::: moniker-end

::: moniker range="vs-2017"

È possibile installare Dotfuscator Community dall'IDE di Visual Studio:

1. Nella barra di ricerca dell'**Avvio veloce** (CTRL + Q) digitare `dotfuscator`. <br/> <br/> ![Avvio veloce](media/install_from_vs_12.png) <br/> <br/>

2. Nei risultati visualizzati nell'Avvio veloce, sotto l'intestazione *Installa*, selezionare **PreEmptive Protection - Dotfuscator (Individual Component)**.
   * Se invece sotto l'intestazione *Menu* viene visualizzato **Strumenti - PreEmptive Protection - Dotfuscator**, Dotfuscator CE è già installato. Selezionare tale opzione per [iniziare][get-started].

3. Verrà visualizzata la finestra del programma di installazione di Visual Studio, preconfigurata per installare Dotfuscator CE.
   > [!NOTE]
   > Potrebbe essere necessario specificare credenziali di amministratore per continuare.

4. Fare clic su *Installa* nella finestra del programma di installazione di Visual Studio. <br/> <br/> ![Fare clic su Installa](media/install_from_vs_345.png) <br/> <br/>

::: moniker-end

Al termine dell'installazione, è possibile [iniziare a usare Dotfuscator Community][get-started].

## <a name="during-visual-studio-installation"></a>Durante l'installazione di Visual Studio

Se non è ancora stato installato Visual Studio, è possibile ottenere il programma di installazione dal [sito Web di Visual Studio][vs-install].
Durante l'esecuzione, verranno visualizzate le opzioni di installazione per l'edizione di Visual Studio selezionata.

::: moniker range="vs-2019"

![Opzioni di installazione](media/install_ui.png)

::: moniker-end

::: moniker range="vs-2017"

![Opzioni di installazione](media/install_ui_17.png)

::: moniker-end

È quindi possibile installare Dotfuscator Community come componente singolo di Visual Studio:

1. Selezionare la scheda **Singoli componenti**.
2. In *Strumenti per il codice*, verificare l'elemento *PreEmptive Protection - Dotfuscator*.<br/> <br/> ![Singoli componenti](media/install_individually_12.png) <br/> <br/>
3. Il pannello *Riepilogo* visualizza *PreEmptive Protection - Dotfuscator* sotto la sezione *Singoli componenti*. <br/> <br/> ![Riquadro Riepilogo](media/install_individually_3.png) <br/> <br/>
4. Configurare le altre impostazioni di installazione come appropriato per l'ambiente.
5. Quando si è pronti per installare Visual Studio, fare clic sul pulsante *Installa*.

Al termine dell'installazione, è possibile iniziare a usare Dotfuscator Community. Per informazioni dettagliate, vedere la [pagina introduttiva della guida dell'utente completa di Dotfuscator Community][get-started].

## <a name="see-also"></a>Vedi anche

[Questo argomento nella guida dell'utente completa di Dotfuscator Community](https://www.preemptive.com/dotfuscator/ce/docs/help/)

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[vs-install]:  https://visualstudio.microsoft.com/downloads/
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html
