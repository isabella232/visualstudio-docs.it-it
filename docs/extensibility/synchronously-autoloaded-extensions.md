---
title: In modo sincrono le estensioni caricate automaticamente
ms.date: 02/16/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 960fd54564bc25a8338461c30cd8a893e277b5a5
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2019
ms.locfileid: "56844581"
---
# <a name="synchronously-autoloaded-extensions"></a>In modo sincrono le estensioni caricate automaticamente

Le estensioni caricate automaticamente in modo sincrono avere un impatto negativo sulle prestazioni di Visual Studio e devono essere convertiti in alternativa, usare autoload asincrona. A partire da Visual Studio 2019 Preview 2, gli utenti saranno informati quando un'estensione è in corso in modo sincrono caricate automaticamente. L'estensione caricherà e funzionare normalmente.

![avviso di compatibilità di estensione](media/extension-compatibility-warning.png)

1. Gli utenti possono fare clic su **altre informazioni** per accedere a questa pagina di informazioni.

3. Gli utenti possono fare clic su **Gestisci prestazioni di** per aprire il [finestra di dialogo Gestione prestazioni](#performance-manager-dialog) che illustra i problemi di prestazioni con le estensioni e finestre degli strumenti.

3. Gli utenti possono fare clic su **non visualizzare più questo messaggio** per ignorarla. Selezionare questa opzione impedisce anche tutte le comunicazioni future tra in modo sincrono le estensioni caricate automaticamente. Gli utenti continueranno a ricevere notifiche su altre funzionalità di Visual Studio.

### <a name="performance-manager-dialog"></a>Finestra di dialogo Gestione delle prestazioni

  ![finestra di dialogo Gestione delle prestazioni](media/performance-manager.png)

Tutte le estensioni caricate in modo sincrono tutti i pacchetti in tutte le sessioni utente verranno visualizzati nei **API deprecate** scheda.

* Gli utenti possono fare clic sui **altre informazioni su questo problema** per raccogliere ulteriori informazioni sulle API deprecate.
* Gli utenti possono contattare i fornitori di estensione per l'avanzamento della migrazione.

Gli autori delle estensioni possono trovare istruzioni per la migrazione dei pacchetti autoload asincrona in [eseguire la migrazione a AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).
