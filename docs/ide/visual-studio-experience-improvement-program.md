---
title: Analisi utilizzo software
description: Informazioni su come gestire le impostazioni di privacy in Visual Studio.
ms.date: 05/21/2018
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6c785b755b64f0dd7e367a01d9c05c1981ea558
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "71693006"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Analisi utilizzo software di Visual Studio

Analisi utilizzo software di Visual Studio è stato pensato per aiutare Microsoft a migliorare nel tempo Visual Studio. Il programma [raccoglie informazioni su errori](../ide/diagnostic-data-collection.md), hardware del computer e modalità d'uso di Visual Studio senza interrompere le attività dell'utente al computer. I dati raccolti consentono a Microsoft di identificare le funzionalità da migliorare. Questo documento illustra come acconsentire o rifiutare esplicitamente di partecipare al programma.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]
> [!NOTE]
> Le impostazioni di telemetria VSCEIP non si applicano a 'Segnala un problema' in Visual Studio.VSCEIP telemetry telemetry sopt in or out settings do not apply to 'Report a Problem' in Visual Studio. Quando si segnalano i registri di un problema vengono raccolti e inviati a Microsoft solo quando si fornisce l'autorizzazione facendo clic su 'Invia'. Se sei interessato a gestire i log prima di inviarlo a "Segnala un problema", consulta [Privacy dei dati](./developer-community-privacy.md) di feedback per ulteriori dettagli.

## <a name="opt-in-or-out"></a>Acconsentire o rifiutare

Analisi utilizzo software di Visual Studio è attivato per impostazione predefinita. È possibile disattivarlo o riattivarlo seguendo queste istruzioni:

1. In Visual Studio scegliere Invia**commenti**e suggerimenti della **Guida** > e quindi selezionare **Impostazioni**.

   Verrà aperta la finestra di dialogo **Analisi utilizzo software di Visual Studio**.

1. Per rifiutare, selezionare **No, non voglio partecipare** e quindi selezionare **OK**. Per acconsentire, selezionare **Sì, voglio partecipare** e quindi selezionare **OK**.

   ![Finestra di dialogo Analisi utilizzo software di Visual Studio](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Impostazioni del Registro di sistema

Se si installa [Build Tools per Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017), sarà necessario aggiornare il Registro di sistema per configurare Analisi utilizzo software di Visual Studio. I clienti aziendali possono creare criteri di gruppo per partecipare o meno ad Analisi utilizzo software di Visual Studio impostando criteri basati sul Registro di sistema.

Le relative impostazioni e chiavi del Registro di sistema sono le seguenti:

::: moniker range="vs-2017"

- In un sistema operativo a 64 bit, chiave = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**
- In un sistema operativo a 32 bit, chiave = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**
- Quando in Criteri di gruppo è attivata, Chiave HKEY_LOCAL_MACHINE **software**

::: moniker-end

::: moniker range=">=vs-2019"

- In un sistema operativo a 64 bit, chiave = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\16.0\SQM**
- In un sistema operativo a 32 bit, chiave = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\16.0\SQM**
- Quando in Criteri di gruppo è attivata, Chiave HKEY_LOCAL_MACHINE **software**

::: moniker-end

Immissione : **Optin**

Valore = (DWORD)

- **0** è stato disattivato (disattivare VSCEIP)
- **1** ha attivato (attivare VSCEIP)

> [!CAUTION]
> Se il Registro di sistema viene modificato in modo non appropriato, il sistema potrebbe venire gravemente danneggiato. Prima di modificare il Registro di sistema, è consigliabile eseguire il backup di tutti i dati importanti disponibili nel computer. È inoltre possibile utilizzare l'opzione di avvio **Ultima configurazione sicura** mente sicura se si verificano problemi dopo l'applicazione di modifiche manuali.

Per altre informazioni sui dati raccolti, elaborati o trasmessi da Analisi utilizzo software di Visual Studio, leggere l'[Informativa sulla privacy di Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>Vedere anche

* [Diagnostic information collected by Visual Studio](diagnostic-data-collection.md) (Informazioni di diagnostica raccolte da Visual Studio)
* [Opzioni per commenti e suggerimenti in Visual Studio](../ide/feedback-options.md)
* [Come segnalare un problema con Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md)
* [Community per sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/)
* [Informativa sulla privacy Microsoft](https://privacy.microsoft.com/privacystatement)
