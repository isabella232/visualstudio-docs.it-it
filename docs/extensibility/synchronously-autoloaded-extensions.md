---
title: Estensioni caricate automaticamente in modo sincrono
description: Informazioni sul comportamento predefinito a partire da Visual Studio 2019, che blocca i pacchetti caricati automaticamente in modo sincrono da qualsiasi estensione.
ms.custom: SEO-VS-2020
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3f7d49c28b94bfa5ef4d23152af5eeb92a0fab12
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144387"
---
# <a name="synchronously-autoloaded-extensions"></a>Estensioni caricate automaticamente in modo sincrono

Le estensioni caricate automaticamente in modo sincrono hanno un impatto negativo sulle prestazioni Visual Studio e devono essere convertite in modo da usare il caricamento automatico asincrono. Per impostazione predefinita, Visual Studio 2019 blocca i pacchetti caricati automaticamente in modo sincrono da qualsiasi estensione e invia una notifica all'utente.

![avviso di compatibilità dell'estensione](media/extension-compatibility-warning-16-1.png.png)

È possibile:

- Fare clic **su Consenti caricamento automatico sincrono per** consentire il caricamento automatico delle estensioni. Per modificare questa impostazione nelle Visual Studio, fare clic su Ambiente, quindi su Estensioni e infine selezionare la casella di controllo "Consenti caricamento automatico sincrono delle estensioni". 

- Fare clic su **Gestisci prestazioni** per aprire la finestra di dialogo [Gestione prestazioni](#performance-manager-dialog) che mostra i problemi di prestazioni relativi alle estensioni e alle finestre degli strumenti.

- Fare clic **su Non visualizzare questo messaggio per le estensioni correnti** per ignorare la notifica ed evitare notifiche future dalle estensioni installate esistenti. Se si aggiunge una nuova estensione che viene caricata automaticamente in modo sincrono, questa notifica verrà visualizzata di nuovo. Si continuerà a ricevere notifiche su altre Visual Studio funzionalità.

## <a name="performance-manager-dialog"></a>Finestra di dialogo Gestione prestazioni

![finestra di dialogo gestione prestazioni](media/performance-manager.png)

Tutte le estensioni che hanno caricato in modo sincrono tutti i pacchetti in qualsiasi sessione utente vengono visualizzate nella **scheda API deprecate.**

* Fare clic **su Altre informazioni su questo problema** per raccogliere altre informazioni sulle API deprecate.
* Contattare i fornitori di estensioni per informazioni sullo stato di avanzamento della migrazione.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Specificare le impostazioni di caricamento automatico sincrono usando Criteri di gruppo

Gli amministratori possono abilitare un Criteri di gruppo consentire il caricamento automatico sincrono. A tale scopo, impostare criteri basati sul Registro di sistema nella chiave seguente:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

Entry = **Allowed**

Valore = (DWORD)
* **0 è** il caricamento automatico sincrono non consentito
* **1 è** consentito il caricamento automatico sincrono

## <a name="extension-authors"></a>Autori di estensioni
Gli autori di estensioni possono trovare istruzioni per la migrazione dei pacchetti al caricamento automatico asincrono in [Eseguire la migrazione ad AsyncPackage.](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration)

## <a name="see-also"></a>Vedi anche
Per altre informazioni sulle impostazioni di caricamento automatico sincrono in Visual Studio 2019, vedere la pagina Comportamento di [caricamento](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/) automatico sincrono.
