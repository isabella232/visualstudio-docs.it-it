---
title: Analisi utilizzo software
description: Informazioni su come gestire le impostazioni di privacy in Visual Studio.
ms.date: 05/21/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74ef70228979d1d302a644cda022d086e710b7c7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54921020"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Analisi utilizzo software di Visual Studio

Analisi utilizzo software di Visual Studio è stato pensato per aiutare Microsoft a migliorare nel tempo Visual Studio. Il programma [raccoglie informazioni su errori](../ide/diagnostic-data-collection.md), hardware del computer e modalità d'uso di Visual Studio senza interrompere le attività dell'utente al computer. I dati raccolti consentono a Microsoft di identificare le funzionalità da migliorare. Questo documento illustra come acconsentire o rifiutare esplicitamente di partecipare al programma.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]

## <a name="opt-in-or-out"></a>Acconsentire o rifiutare

Analisi utilizzo software di Visual Studio è attivato per impostazione predefinita. È possibile disattivarlo o riattivarlo seguendo queste istruzioni:

1. Avviare Visual Studio.

1. Nel menu **?** scegliere **Invia commenti e suggerimenti** e quindi selezionare **Impostazioni**.

   Verrà aperta la finestra di dialogo **Analisi utilizzo software di Visual Studio**.

1. Per rifiutare, selezionare **No, non voglio partecipare** e quindi selezionare **OK**.
   Per acconsentire, selezionare **Sì, voglio partecipare** e quindi selezionare **OK**.

   ![Finestra di dialogo Analisi utilizzo software di Visual Studio](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Impostazioni del Registro di sistema

Se si installa [Build Tools per Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017), sarà necessario aggiornare il Registro di sistema per configurare Analisi utilizzo software di Visual Studio. I clienti aziendali possono creare criteri di gruppo per partecipare o meno ad Analisi utilizzo software di Visual Studio impostando criteri basati sul Registro di sistema.

Le chiavi e le impostazioni del Registro di sistema sono le seguenti:

In un sistema operativo a 64 bit Key = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM** In un sistema operativo a 32 bit Key = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM** Quando è abilitato Criteri di gruppo Key = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

Entry = **OptIn**

Valore = (DWORD)
- **0** indica il rifiuto (disattiva Analisi utilizzo software di Visual Studio)
- **1** indica il consenso (attiva Analisi utilizzo software di Visual Studio)

> [!CAUTION]
> Modifiche non corrette al Registro di sistema potrebbero danneggiare gravemente il sistema. Prima di modificare il Registro di sistema, è necessario eseguire il backup dei dati importanti sul computer. Se si riscontrano problemi dopo l'applicazione di modifiche manuali, è anche possibile usare l'opzione di avvio **Ultima configurazione valida nota**.

Per altre informazioni sui dati raccolti, elaborati o trasmessi da Analisi utilizzo software di Visual Studio, leggere l'[Informativa sulla privacy di Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>Vedere anche

* [Diagnostic information collected by Visual Studio](diagnostic-data-collection.md) (Informazioni di diagnostica raccolte da Visual Studio)
* [Comunicazioni con Microsoft](../ide/talk-to-us.md)
* [Come segnalare un problema con Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)
* [Community di sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/)
* [Informativa sulla privacy di Microsoft](https://privacy.microsoft.com/privacystatement)
