---
title: Estensioni caricate automaticamente in modo sincrono
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab62d235fd6ed4e47e765fc23868acd5c56efcb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699377"
---
# <a name="synchronously-autoloaded-extensions"></a>Estensioni caricate automaticamente in modo sincrono

Le estensioni caricate automaticamente in modo sincrono hanno un impatto negativo sulle prestazioni di Visual Studio e devono essere convertite per usare invece il caricamento automatico asincrono. Per impostazione predefinita, Visual Studio 2019 blocca i pacchetti caricati automaticamente in modo sincrono da qualsiasi estensione e notifica all'utente.

![avviso di compatibilità delle estensioni](media/extension-compatibility-warning-16-1.png.png)

È possibile:

- Fare clic su **Consenti caricamento automatico sincrono** per consentire il caricamento automatico delle estensioni. Per modificare questa impostazione nelle opzioni di Visual Studio, fare clic su Ambiente, quindi su Estensioni e quindi selezionare la casella di controllo "Consenti caricamento automatico sincrono delle estensioni". 

- Fare clic su **Gestisci prestazioni** per aprire la finestra di [dialogo Performance Manager](#performance-manager-dialog) che mostra i problemi di prestazioni con le estensioni e le finestre degli strumenti.

- Fare clic su **Non visualizzare questo messaggio per le estensioni correnti per** ignorare la notifica e impedire notifiche future dalle estensioni installate esistenti. Se si aggiunge una nuova estensione che viene caricata automaticamente in modo sincrono, verrà visualizzata di nuovo questa notifica. Continuerai a ricevere notifiche su altre funzionalità di Visual Studio.You will continue to get notifications about other Visual Studio features.

## <a name="performance-manager-dialog"></a>Finestra di dialogo Gestione prestazioni

![Finestra di dialogo Gestione prestazioni](media/performance-manager.png)

Tutte le estensioni che hanno caricato in modo sincrono tutti i pacchetti in tutte le sessioni utente vengono visualizzate nella scheda **API deprecate.**

* Fare clic su **Ulteriori informazioni su questo problema** per raccogliere ulteriori informazioni sulle API deprecate.
* Contattare i fornitori di estensioni per l'avanzamento della migrazione.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Specificare le impostazioni di caricamento automatico sincrono tramite Criteri di gruppo

Gli amministratori possono abilitare criteri di gruppo per consentire il caricamento automatico sincrono. A tale scopo, impostare criteri basati sul Registro di sistema nella chiave seguente:

**HKEY_LOCAL_MACHINE SOFTWARE, Criteri di gruppo, Microsoft Visual Studio SynchronousAutoload**

Immissione - **Consentito**

Valore = (DWORD)
* **0** è il caricamento automatico sincrono non consentito
* **1** è consentito il caricamento automatico sincrono

## <a name="extension-authors"></a>Autori di estensioni
Gli autori di estensioni possono trovare istruzioni per la migrazione dei pacchetti per il caricamento automatico asincrono [in Esegui migrazione a AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="see-also"></a>Vedere anche
Per altre informazioni sulle impostazioni di caricamento automatico sincrono in Visual Studio 2019, vedere la pagina Comportamento caricamento [automatico sincrono.](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/)
