---
title: Aggiornare un'estensione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0d1464cdd2be79cd93a3e98bcf8769e8f4b8b89f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840302"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Procedura: Aggiornare un'estensione di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile aggiornare un'estensione di Visual Studio nel sistema usando **estensioni e aggiornamenti** per installare la versione aggiornata. Se si crea una versione aggiornata di un'estensione, è possibile significarla come aggiornata incrementando il numero di versione nel manifesto VSIX.

 Gli aggiornamenti vengono installati quando il manifesto VSIX dell'estensione in ingresso ha lo stesso `ID` valore di quello installato e un numero più alto `Version` . Se il `Version` numero è uguale o inferiore, il pacchetto non può essere installato. Se i `ID` valori non corrispondono, il pacchetto non ancora installato viene riconosciuto come estensione distinta.

 Per evitare conflitti durante lo sviluppo, si consiglia di disinstallare le versioni precedenti delle estensioni in corso e disinstallare o disabilitare altre estensioni potenzialmente in conflitto.

### <a name="to-update-an-extension-on-your-system"></a>Per aggiornare un'estensione nel sistema

1. Dal menu **Strumenti** scegliere **Estensioni e aggiornamenti**.

2. Nel riquadro sinistro fare clic su **aggiornamenti**.

3. Nel riquadro centrale fare clic sull'aggiornamento che si desidera installare.

     Il numero di versione dell'estensione aggiornata viene visualizzato nel riquadro destro, insieme ad altre informazioni.

4. Nella parte inferiore del riquadro destro fare clic su **Aggiorna**.

### <a name="to-publish-an-update-of-an-extension"></a>Per pubblicare un aggiornamento di un'estensione

1. In Visual Studio aprire la soluzione per l'estensione che si desidera aggiornare. Apportare le modifiche.

    > [!IMPORTANT]
    > Tutte le estensioni utente senza segno non vengono aggiornate automaticamente. È necessario firmare sempre le estensioni.

2. In **Esplora soluzioni**aprire source. Extension. manifest.

3. In Progettazione manifesto aumentare il valore del numero nel campo **versione** .

4. Salvare la soluzione e compilarla.

5. Caricare il nuovo file VSIX (nella cartella \bin\Debug\ del progetto) nel sito Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

     Quando un utente con una versione precedente dell'estensione apre **estensioni e aggiornamenti**, la nuova versione verrà visualizzata nell'elenco degli **aggiornamenti** , a condizione che lo strumento sia impostato in modo da cercare automaticamente gli aggiornamenti.

     È possibile abilitare o disabilitare il controllo automatico degli aggiornamenti nella parte inferiore del riquadro **aggiornamenti** (**Abilita/Disabilita rilevamento automatico degli aggiornamenti disponibili**), che modifica l'impostazione **Verifica aggiornamenti** in **strumenti/opzioni/ambiente/estensioni e aggiornamenti**.

    > [!NOTE]
    > A partire da Visual Studio 2015 Update 2, è possibile specificare in **Strumenti / Opzioni / Ambiente / Estensioni e aggiornamenti** se gli aggiornamenti automatici devono essere installati per le estensioni per utente, per tutte le estensioni utente o entrambe le opzioni (impostazione predefinita).

## <a name="see-also"></a>Vedere anche
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md) [ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
