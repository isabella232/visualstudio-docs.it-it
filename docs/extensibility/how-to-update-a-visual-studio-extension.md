---
title: "Procedura: Aggiornare un'estensione Visual Studio | Microsoft Docs"
description: Informazioni su come aggiornare un'Visual Studio nel sistema usando Estensioni e aggiornamenti per installare la versione aggiornata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c69ab2bedfda4394c0256db7040de39e8a520ca4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124815"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Procedura: Aggiornare un'Visual Studio predefinita
È possibile aggiornare un'Visual Studio nel sistema usando **Estensioni e aggiornamenti** per installare la versione aggiornata. Se si crea una versione aggiornata di un'estensione, è possibile indicarla come aggiornata incrementando il numero di versione nel manifesto VSIX.

 Gli aggiornamenti vengono installati quando il manifesto VSIX dell'estensione in ingresso ha lo stesso di quello installato `ID` e un numero `Version` superiore. Se il `Version` numero è uguale o inferiore, il pacchetto non può essere installato. Se i valori non corrispondono, il pacchetto non ancora installato viene `ID` riconosciuto come estensione separata.

 Per evitare conflitti durante lo sviluppo, è consigliabile disinstallare le versioni precedenti delle estensioni in corso e disinstallare o disabilitare eventuali altre estensioni potenzialmente in conflitto.

## <a name="to-update-an-extension-on-your-system"></a>Per aggiornare un'estensione nel sistema

1. Dal menu **Strumenti** scegliere **Estensioni e aggiornamenti**.

2. Nel riquadro sinistro fare clic su **Aggiornamenti**.

3. Nel riquadro centrale fare clic sull'aggiornamento da installare.

     Il numero di versione dell'estensione aggiornata viene visualizzato nel riquadro destro, insieme ad altre informazioni.

4. Nella parte inferiore del riquadro destro fare clic su **Aggiorna.**

## <a name="to-publish-an-update-of-an-extension"></a>Per pubblicare un aggiornamento di un'estensione

1. In Visual Studio aprire la soluzione per l'estensione che si vuole aggiornare. Apportare le modifiche.

    > [!IMPORTANT]
    > Tutte le estensioni utente non firmate non vengono aggiornate automaticamente. È consigliabile firmare sempre le estensioni.

2. In **Esplora soluzioni** aprire *source.extension.manifest.*

3. Nella finestra di progettazione del manifesto aumentare il valore del numero nel **campo** Versione.

4. Salvare la soluzione e compilarla.

5. Upload il nuovo file con estensione *vsix* (nella cartella *\bin\Debug del progetto) nel sito \* Web Visual Studio [Marketplace.](https://marketplace.visualstudio.com/vs)

     Quando un utente che dispone di una versione precedente dell'estensione apre  Estensioni e aggiornamenti **,** la nuova versione verrà visualizzata nell'elenco Aggiornamenti, a condizione che lo strumento sia impostato per la ricerca automatica degli aggiornamenti.

     È possibile abilitare o disabilitare il controllo  automatico degli aggiornamenti nella parte inferiore del  riquadro Aggiornamenti (**Abilita/disabilita** il rilevamento automatico degli aggiornamenti disponibili), che modifica l'impostazione Verifica la disponibilità di aggiornamenti **in** Strumenti Opzioni Estensioni ambiente  >    >    >  **e aggiornamenti**.

    > [!NOTE]
    > A partire da Visual Studio 2015 Update 2, è possibile specificare **(in** Strumenti Opzioni Estensioni ambiente e aggiornamenti ) se si desiderano gli aggiornamenti automatici per le estensioni per utente, tutte le estensioni utente o entrambe  >    >    >  (impostazione predefinita).

## <a name="see-also"></a>Vedi anche
- [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Trovare e usare le Visual Studio seguenti](../ide/finding-and-using-visual-studio-extensions.md)
