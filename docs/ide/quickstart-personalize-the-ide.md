---
title: Impostare il tema Visual Studio scuro e modificare i colori del testo
description: Informazioni su come modificare l'impostazione Visual Studio tema colori in modalità scura e modificare i colori dei caratteri nell'editor di codice.
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 945a2e1c7650e43afa9d9e0562371545ca09746d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137223"
---
# <a name="how-to-personalize-the-visual-studio-ide-and-the-editor"></a>Procedura: Personalizzare l'IDE Visual Studio e l'editor

In questo articolo di procedura verrà personalizzato il tema Visual Studio dal tema blu predefinito al tema scuro. Verranno quindi personalizzati i colori per due diversi tipi di testo nell'editor di codice.

::: moniker range="vs-2017"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

## <a name="set-the-color-theme-for-the-ide"></a>Impostare il tema colori per l'IDE

Il tema colori predefinito per l'interfaccia utente di Visual Studio è denominato **Blu**. Per questa esercitazione verrà cambiato in **Scuro**.

1. Nella barra dei menu, ovvero la riga dei menu con **File** e **Modifica**, scegliere **Strumenti** > **Opzioni**.

1. Nella pagina **delle**  >  **opzioni Generale** ambiente modificare la selezione di **Tema** colori in **Scuro** e quindi scegliere **OK.**

   Il tema colori per l'intero ambiente di sviluppo di Visual Studio (IDE) diventa **scuro**.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 con tema scuro](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019 con tema scuro](media/vs-2019/dark-theme.png)

   ::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> È possibile installare temi predefiniti aggiuntivi installando **Visual Studio Color Theme Editor** da [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Dopo aver installato questo strumento, nell'elenco a discesa Tema colori vengono visualizzati temi colori aggiuntivi. 

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> È possibile creare temi personalizzati installando la finestra Visual Studio **Color Theme Designer (Progettazione** temi colori) [Visual Studio Marketplace.](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner)

::: moniker-end

## <a name="change-text-colors-in-the-editor"></a>Modificare i colori del testo nell'editor

Si vedrà ora come personalizzare alcuni colori del testo per l'editor. Prima di tutto, creare un nuovo file XML per visualizzare i colori predefiniti.

1. Dalla barra dei menu scegliere **File**  >  **Nuovo**  >  **file.**

1. Nella finestra di dialogo **Nuovo file**, nella categoria **Generale**, scegliere **File XML** e quindi scegliere **Apri**.

1. Incollare il codice XML seguente sotto la riga che contiene `<?xml version="1.0" encoding="utf-8"?>`.

   ```xml
   <Catalog>
     <Book id="bk101">
     <Author>Garghentini, Davide</Author>
     <Title>XML Developer's Guide</Title>
     <Genre>Computer</Genre>
     <Price>44.95</Price>
     <PublishDate>2000-10-01</PublishDate>
     <Description>
       An in-depth look at creating applications with XML.
     </Description>
   </Book>
   <Book id="bk102">
     <Author>Garcia, Debra</Author>
     <Title>Midnight Rain</Title>
     <Genre>Fantasy</Genre>
     <Price>5.95</Price>
     <PublishDate>2000-12-16</PublishDate>
     <Description>
       A former architect battles corporate zombies, an evil
       sorceress, and her own childhood to become queen of the world.
     </Description>
   </Book>
   </Catalog>
   ```

   Si noti che i numeri di riga sono di colore blu-turchese e gli attributi XML, ad esempio `id="bk101"`, di colore azzurro. Verranno di seguito modificati i colori del testo per questi elementi.

   ![Colori dei caratteri nei file XML](media/quickstart-personalize-xml-file.png)

1. Per aprire la finestra di dialogo **Opzioni**, scegliere **Strumenti** > **Opzioni** dalla barra dei menu.

1. In **Ambiente** scegliere la categoria **Tipi di carattere e colori**.

   Si noti che il testo in **Mostra impostazioni per** indica Editor **di** &mdash; testo. Espandere l'elenco a discesa per visualizzare l'elenco completo delle posizioni in cui è possibile personalizzare i tipi di carattere e il colore del testo.

1. Per modificare il colore del testo dei numeri di riga, in **Elementi visualizzati** scegliere **Numero di riga**. Nella casella **Primo piano elemento** scegliere **Verde oliva**.

   ![Finestra di dialogo Opzioni, categoria Tipi di carattere e colori](media/quickstart-personalize-line-number-color.png)

   Alcuni linguaggi dispongono di impostazioni proprie per i tipi di carattere e i colori. Se ad esempio uno sviluppatore C++ desidera modificare il colore utilizzato per le funzioni, può cercare **Funzioni C++** nell'elenco **Elementi visualizzati**.

1. Prima uscire dalla finestra di dialogo, verrà modificato anche il colore degli attributi XML. Nell'elenco **Elementi visualizzati** scorrere verso il basso fino ad **Attributo XML** e selezionarlo. Nella casella **Primo piano elemento** scegliere **Verde limone**. Scegliere **OK** per salvare le selezioni e chiudere la finestra di dialogo.

   I numeri di riga sono ora di colore verde oliva e gli attributi XML di un vivace verde limone. Se si apre un altro tipo di file, ad esempio un file di codice C# o C++, si noterà che per la visualizzazione dei numeri di riga viene usato il colore verde oliva anche in questi file.

   ![File XML con i nuovi colori dei caratteri](media/quickstart-personalize-xml-file-new-colors.png)

Sono stati presentati solo un paio di modi per personalizzare i colori in Visual Studio. Ci auguriamo che si esplorino [](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) le altre opzioni di personalizzazione nella finestra di dialogo Opzioni per Visual Studio proprie.

## <a name="see-also"></a>Vedi anche

- [Procedura: Modificare tipi di carattere, colori e temi in Visual Studio](../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
- [Procedura: Modificare maiuscole/minuscole nell'editor](../ide/how-to-change-text-case-in-the-editor.md)
- [Panoramica dell'ambiente IDE di Visual Studio](../get-started/visual-studio-ide.md)
