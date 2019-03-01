---
title: Estensioni caricate automaticamente in modo sincrono
ms.date: 02/16/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad3831fb06d23f622f85a55f5efd0a5650ca5e47
ms.sourcegitcommit: 62149c96de0811415e99bb1e0194e76c320e1a1e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2019
ms.locfileid: "57007163"
---
# <a name="synchronously-autoloaded-extensions"></a>Estensioni caricate automaticamente in modo sincrono

Le estensioni caricate automaticamente in modo sincrono avere un impatto negativo sulle prestazioni di Visual Studio e devono essere convertiti in alternativa, usare autoload asincrona. A partire da Visual Studio 2019 Preview 2, gli utenti vengono informati quando un'estensione è in corso in modo sincrono caricate automaticamente. L'estensione caricherà e funzionare normalmente.

![avviso di compatibilità di estensione](media/extension-compatibility-warning.png)

Gli utenti possono:

- Fare clic su **altre informazioni** per accedere a questa pagina di informazioni.

- Fare clic su **Gestisci prestazioni di** per aprire il [finestra di dialogo Gestione prestazioni](#performance-manager-dialog) che illustra i problemi di prestazioni con le estensioni e finestre degli strumenti.

- Fare clic su **non visualizzare più questo messaggio** per ignorarla. Selezionare questa opzione impedisce inoltre tutte le comunicazioni future tra in modo sincrono le estensioni caricate automaticamente. Gli utenti continueranno a ricevere notifiche su altre funzionalità di Visual Studio.

### <a name="performance-manager-dialog"></a>Finestra di dialogo Gestione delle prestazioni

![finestra di dialogo Gestione delle prestazioni](media/performance-manager.png)

Tutte le estensioni caricate in modo sincrono tutti i pacchetti in tutte le sessioni utente vengono visualizzati nei **API deprecate** scheda.

* Gli utenti possono fare clic sui **altre informazioni su questo problema** per raccogliere ulteriori informazioni sulle API deprecate.
* Gli utenti possono contattare i fornitori di estensione per l'avanzamento della migrazione.

Gli autori delle estensioni possono trovare istruzioni per la migrazione dei pacchetti autoload asincrona in [eseguire la migrazione a AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).
