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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435893"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Procedura: Aggiornare un'estensione di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile aggiornare un'estensione di Visual Studio nel sistema mediante **estensioni e aggiornamenti** per installare la versione aggiornata. Se si crea una versione aggiornata di un'estensione, è possibile segnalare l'aggiornamento incrementando il numero di versione nel manifesto VSIX.

 Gli aggiornamenti vengono installati quando il manifesto VSIX dell'estensione in ingresso con lo stesso `ID` come un valore più alto e quello installato `Version` numero. Se il `Version` numero è uguale o inferiore, il pacchetto non può essere installato. Se il `ID` valori non corrispondono, il pacchetto che non è ancora installato è riconosciuto come un'estensione separata.

 Per evitare conflitti durante lo sviluppo, è consigliabile disinstallare le versioni precedenti delle estensioni in corso e anche disinstallare o disabilitare tutte le altre estensioni potenzialmente in conflitto.

### <a name="to-update-an-extension-on-your-system"></a>Per aggiornare un'estensione del sistema

1. Nel menu **Strumenti** fare clic su **Estensioni e aggiornamenti**.

2. Nel riquadro sinistro, fare clic su **aggiornamenti**.

3. Nel riquadro centrale, fare clic sull'aggiornamento da installare.

     Il numero di versione dell'estensione aggiornato viene visualizzato nel riquadro di destra, insieme ad altre informazioni.

4. Nella parte inferiore del riquadro destro, fare clic su **Update**.

### <a name="to-publish-an-update-of-an-extension"></a>Per pubblicare un aggiornamento di un'estensione

1. In Visual Studio, aprire la soluzione per l'estensione da aggiornare. Apportare le modifiche.

    > [!IMPORTANT]
    > Valore unsigned che tutte le estensioni utente non vengono aggiornate automaticamente. È sempre necessario firmare le estensioni.

2. Nelle **Esplora soluzioni**, aprire source.extension.manifest.

3. Nella finestra di progettazione manifesto, aumentare il valore del numero nel **versione** campo.

4. Salvare la soluzione e compilarla.

5. Caricare il nuovo file con estensione VSIX (nella cartella \bin\Debug\ del progetto) per il [Visual Studio Marketplace](https://marketplace.visualstudio.com/) sito Web.

     Quando si apre un utente che dispone di una versione precedente dell'estensione **estensioni e aggiornamenti**, la nuova versione verrà visualizzato nei **aggiornamenti** elencare, condizione che lo strumento è impostato per la ricerca di aggiornamenti.

     È possibile abilitare o disabilitare il controllo automatico per gli aggiornamenti nella parte inferiore della **aggiornamenti** riquadro (**abilitare/disabilitare il rilevamento automatico degli aggiornamenti disponibili**), quali modifiche di **verificare la presenza di gli aggiornamenti** impostazione **Strumenti / opzioni / ambiente / estensioni e aggiornamenti**.

    > [!NOTE]
    > A partire da Visual Studio 2015 Update 2, è possibile specificare in **Strumenti / Opzioni / Ambiente / Estensioni e aggiornamenti** se gli aggiornamenti automatici devono essere installati per le estensioni per utente, per tutte le estensioni utente o entrambe le opzioni (impostazione predefinita).

## <a name="see-also"></a>Vedere anche
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md) [ricerca e uso di estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
