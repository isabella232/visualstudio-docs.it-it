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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699377"
---
# <a name="synchronously-autoloaded-extensions"></a>Estensioni caricate automaticamente in modo sincrono

Le estensioni autocaricate in modo sincrono hanno un impatto negativo sulle prestazioni di Visual Studio e devono essere convertite in alternativa all'utilizzo di autoload asincrono. Per impostazione predefinita, Visual Studio 2019 blocca i pacchetti caricati in modo sincrono da qualsiasi estensione e invia una notifica all'utente.

![avviso di compatibilità dell'estensione](media/extension-compatibility-warning-16-1.png.png)

È possibile scegliere:

- Fare clic su **Consenti autoload sincrono** per consentire le estensioni di autoload. Per modificare questa impostazione nelle opzioni di Visual Studio, fare clic su ambiente, quindi su estensioni, quindi selezionare la casella di controllo "Consenti autoload sincrono di estensioni". 

- Fare clic su **Gestisci prestazioni** per aprire la [finestra di dialogo Gestione prestazioni](#performance-manager-dialog) che mostra i problemi di prestazioni con le estensioni e le finestre degli strumenti.

- Fare clic su **non visualizzare questo messaggio per le estensioni correnti** per ignorare la notifica e impedire notifiche future dalle estensioni installate esistenti. Se si aggiunge una nuova estensione che viene caricata in modo sincrono, la notifica verrà visualizzata nuovamente. Si continuerà a ricevere notifiche sulle altre funzionalità di Visual Studio.

## <a name="performance-manager-dialog"></a>Finestra di dialogo Gestione prestazioni

![finestra di dialogo Gestione prestazioni](media/performance-manager.png)

Tutte le estensioni che hanno caricato in modo sincrono tutti i pacchetti in qualsiasi sessione utente vengono visualizzate nella scheda **API deprecate** .

* Fare clic su **altre informazioni su questo problema** per raccogliere altre informazioni sulle API deprecate.
* Per lo stato della migrazione, contattare i fornitori di estensioni.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Specificare le impostazioni di caricamento automatico sincrono tramite criteri di gruppo

Gli amministratori possono abilitare un Criteri di gruppo per consentire l'autoload sincrono. A tale scopo, impostare criteri basati sul Registro di sistema nella chiave seguente:

**HKEY_LOCAL_MACHINE \SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

Entry = **consentito**

Valore = (DWORD)
* **0** è un autoload sincrono non consentito
* **1** è consentito un autoload sincrono

## <a name="extension-authors"></a>Autori di estensioni
Gli autori di estensioni sono in grado di trovare istruzioni per la migrazione di pacchetti a autoload asincrono alla [migrazione a AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="see-also"></a>Vedere anche
Per altre informazioni sulle impostazioni di autoload sincrono in Visual Studio 2019, vedere la pagina [comportamento di autoload sincrono](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/) .
