---
title: Analisi utilizzo software
description: Informazioni su come gestire le impostazioni di privacy in Visual Studio.
ms.date: 05/21/2018
ms.topic: conceptual
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 251b440853520bc18e918082cc9607ed2a15ebec
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2021
ms.locfileid: "129635620"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Analisi utilizzo software di Visual Studio

Analisi utilizzo software di Visual Studio è stato pensato per aiutare Microsoft a migliorare nel tempo Visual Studio. Il programma [raccoglie informazioni su errori](../ide/diagnostic-data-collection.md), hardware del computer e modalità d'uso di Visual Studio senza interrompere le attività dell'utente al computer. I dati raccolti consentono a Microsoft di identificare le funzionalità da migliorare. Questo documento illustra come acconsentire o rifiutare esplicitamente di partecipare al programma. Quando si rifiuta esplicitamente, si rifiuta esplicitamente la raccolta **dei dati** di diagnostica facoltativi. È necessaria una raccolta **di** dati di diagnostica per assicurarsi che Visual Studio sia sicuro, aggiornato e funzioni come previsto. La raccolta dei dati di diagnostica richiesta non verrà influenzata dalla scelta di rifiutare esplicitamente VSCEIP.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]
> [!NOTE]
> Le impostazioni di consenso esplicito o di rifiuto della telemetria VSCEIP non si applicano a "Segnala un problema" in Visual Studio. Quando si segnala un problema, i log vengono raccolti e inviati a Microsoft solo quando si fornisce l'autorizzazione facendo clic su "Invia". Se si è interessati alla gestione dei log prima dell'invio a "Segnala un problema", vedere Privacy dei dati di [feedback](./developer-community-privacy.md) per altri dettagli.

## <a name="opt-in-or-out"></a>Acconsentire o rifiutare

Analisi utilizzo software di Visual Studio è attivato per impostazione predefinita. È possibile disattivarlo o riattivarlo seguendo queste istruzioni:

1. Nella Visual Studio, scegliere **Help**  >  **Send Feedback (Invia commenti e suggerimenti)** e quindi **selezionare Impostazioni**.

   Verrà aperta la finestra di dialogo **Analisi utilizzo software di Visual Studio**.

1. Per rifiutare, selezionare **No, non voglio partecipare** e quindi selezionare **OK**. Per acconsentire, selezionare **Sì, voglio partecipare** e quindi selezionare **OK**.

   ![Finestra di dialogo Analisi utilizzo software di Visual Studio](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Impostazioni del Registro di sistema

Se si installa [Build Tools per Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017), sarà necessario aggiornare il Registro di sistema per configurare Analisi utilizzo software di Visual Studio. I clienti aziendali possono creare criteri di gruppo per partecipare o meno ad Analisi utilizzo software di Visual Studio impostando criteri basati sul Registro di sistema.

Le relative impostazioni e chiavi del Registro di sistema sono le seguenti:

::: moniker range="vs-2017"

- In un sistema operativo a 64 bit, chiave = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**
- In un sistema operativo a 32 bit, chiave = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**
- Quando Criteri di gruppo abilitata, Chiave = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

::: moniker range=">=vs-2019"

- In un sistema operativo a 64 bit, chiave = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\16.0\SQM**
- In un sistema operativo a 32 bit, chiave = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\16.0\SQM**
- Quando Criteri di gruppo abilitata, Chiave = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

Entry = **OptIn**

Valore = (DWORD)

- **0** viene rifiutato esplicitamente (disattivare VSCEIP)
- **1** è stato acconsentito esplicitamente (attivare VSCEIP)

> [!CAUTION]
> La modifica non corretta del Registro di sistema potrebbe danneggiare gravemente il sistema. Prima di apportare modifiche al Registro di sistema, si consiglia di effettuare il backup di tutti i dati importanti presenti sul computer. È anche possibile usare **l'opzione di** avvio Ultima configurazione valida nota se si verificano problemi dopo l'applicazione di modifiche manuali.

Per altre informazioni sui dati raccolti, elaborati o trasmessi da Analisi utilizzo software di Visual Studio, leggere l'[Informativa sulla privacy di Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>Vedi anche

* [Diagnostic information collected by Visual Studio](diagnostic-data-collection.md) (Informazioni di diagnostica raccolte da Visual Studio)
* [Come segnalare un problema con Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md)
* [Visual Studio Developer Community](https://developercommunity.visualstudio.com/home)
* [Informativa sulla privacy di Microsoft](https://privacy.microsoft.com/privacystatement)
