---
title: "Procedura: aggiornare un'estensione di Visual Studio Documenti Microsoft"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 266c0a49db1bca03cec0eb68301445102173df3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710659"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Procedura: aggiornare un'estensione di Visual StudioHow to: Update a Visual Studio extension
È possibile aggiornare un'estensione di Visual Studio nel sistema utilizzando **estensioni e aggiornamenti** per installare la versione aggiornata. Se si crea una versione aggiornata di un'estensione, è possibile indicarla come aggiornata incrementando il numero di versione nel manifesto VSIX.

 Gli aggiornamenti vengono installati quando il manifesto VSIX dell'estensione in ingresso ha lo stesso `ID` numero di quello installato e un numero superiore. `Version` Se `Version` il numero è uguale o inferiore, il pacchetto non può essere installato. Se `ID` i valori non corrispondono, il pacchetto non ancora installato viene riconosciuto come estensione separata.

 Per evitare conflitti durante lo sviluppo, è consigliabile disinstallare le versioni precedenti delle estensioni in corso e disinstallare o disabilitare eventuali altre estensioni potenzialmente in conflitto.

## <a name="to-update-an-extension-on-your-system"></a>Per aggiornare un'estensione nel sistema

1. Nel menu **Strumenti** fare clic su **Estensioni e aggiornamenti**.

2. Nel riquadro sinistro fare clic su **Aggiornamenti**.

3. Nel riquadro centrale fare clic sull'aggiornamento che si desidera installare.

     Il numero di versione dell'estensione aggiornata viene visualizzato nel riquadro di destra, insieme ad altre informazioni.

4. Nella parte inferiore del riquadro destro fare clic su **Aggiorna**.

## <a name="to-publish-an-update-of-an-extension"></a>Per pubblicare un aggiornamento di un'estensione

1. In Visual Studio aprire la soluzione per l'estensione da aggiornare. Apportare le modifiche.

    > [!IMPORTANT]
    > Non firmato tutte le estensioni utente non vengono aggiornate automaticamente. Dovresti sempre firmare le tue estensioni.

2. In **Esplora soluzioni**aprire *source.extension.manifest*.

3. Nella finestra di progettazione del manifesto, aumentare il valore del numero nel campo **versione** .

4. Salvare la soluzione e compilarla.

5. Caricare il nuovo file *con estensione vsix* \* (nella cartella .bin-Debug del progetto) nel sito Web di [Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

     Quando un utente con una versione precedente dell'estensione apre **Estensioni e aggiornamenti**, la nuova versione verrà visualizzata nell'elenco **Degli aggiornamenti,** a condizione che lo strumento sia impostato per cercare automaticamente gli aggiornamenti.

     È possibile attivare o disattivare il controllo automatico degli aggiornamenti nella parte inferiore del riquadro **Aggiornamenti** (**Abilita/disabilita rilevamento automatico degli aggiornamenti disponibili**), che modifica l'impostazione **Controlla aggiornamenti** in **Strumenti** > **Opzioni** > **Estensioni e aggiornamenti dell'ambiente****Environment** > .

    > [!NOTE]
    > A partire da Visual Studio 2015 Update 2, è possibile specificare (in **Strumenti** > **Opzioni** > **Estensioni di ambiente** > **e aggiornamenti**) se si desidera che gli aggiornamenti automatici per le estensioni per utente, tutte le estensioni utente o entrambi (impostazione predefinita).

## <a name="see-also"></a>Vedere anche
- [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Trovare e usare le estensioni di Visual StudioFind and using Visual Studio extensions](../ide/finding-and-using-visual-studio-extensions.md)
