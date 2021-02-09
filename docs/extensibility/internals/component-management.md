---
title: Gestione dei componenti | Microsoft Docs
description: Informazioni su come gestire i componenti di Windows Installer quando si crea un programma di installazione VSPackage in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 44ee1a3afe313cdc11bb28e0a24a89e3e3ad7f0c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852726"
---
# <a name="component-management"></a>Gestione dei componenti
Le unità di attività nel Windows Installer sono definite componenti Windows Installer (talvolta denominati WICs o Just Components). Un GUID identifica ogni WIC, ovvero l'unità di base dell'installazione e il conteggio dei riferimenti per le configurazioni che utilizzano Windows Installer.

 Sebbene sia possibile usare diversi prodotti per creare il programma di installazione di VSPackage, questa discussione presuppone l'uso di file di Windows Installer (*MSI*). Quando si crea il programma di installazione, è necessario gestire correttamente la distribuzione di file in modo che il conteggio dei riferimenti corretto avvenga sempre. Di conseguenza, diverse versioni del prodotto non interferiscono o si interromperanno tra loro in una combinazione di scenari di installazione e disinstallazione.

 In Windows Installer, il conteggio dei riferimenti viene eseguito a livello di componente. È necessario organizzare con attenzione le risorse, ovvero file, voci del registro di sistema e così via, in componenti. Esistono altri livelli di organizzazione, ad esempio moduli, funzionalità e prodotti, che possono essere utili in scenari diversi. Per ulteriori informazioni, vedere [nozioni di base su Windows Installer](../../extensibility/internals/windows-installer-basics.md).

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Linee guida per la creazione dell'installazione side-by-side

- Creare file e chiavi del registro di sistema condivisi tra le versioni nei propri componenti.

     In questo modo è possibile utilizzarli facilmente nella prossima versione. Ad esempio, le librerie dei tipi registrate globalmente, le estensioni di file, altri elementi registrati in **HKEY_CLASSES_ROOT** e così via.

- Raggruppare i componenti condivisi in moduli unione distinti.

     Questa strategia consente di creare correttamente un'installazione side-by-side in futuro.

- Installare i file condivisi e le chiavi del registro di sistema usando gli stessi componenti Windows Installer tra le versioni.

     Se si usa un componente diverso, i file e le voci del registro di sistema vengono disinstallati quando viene disinstallato un pacchetto VSPackage con versione, ma è ancora installato un altro pacchetto VSPackage.

- Non combinare elementi condivisi e con versione nello stesso componente.

     In questo modo è Impossibile installare gli elementi condivisi in un percorso globale e gli elementi con controllo delle versioni in posizioni isolate.

- Non sono disponibili chiavi del registro di sistema condivise che puntano a file con versione.

     In tal caso, le chiavi condivise verranno sovrascritte quando viene installato un altro pacchetto VSPackage con versione. Dopo la rimozione della seconda versione, il file a cui punta la chiave non è più disponibile.

## <a name="see-also"></a>Vedi anche
- [Scegliere tra VSPackage condivisi e con versione](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Scenari di installazione di VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
