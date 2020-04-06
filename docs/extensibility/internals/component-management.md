---
title: Gestione dei componenti Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5dcac9fb14a83021b852be2c52436fcdca84bf5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709333"
---
# <a name="component-management"></a>Gestione dei componenti
Le unità di attività in Windows Installer sono denominate componenti di Windows Installer (talvolta denominati WIC o solo componenti). Un GUID identifica ogni WIC, ovvero l'unità di base di installazione e conteggio dei riferimenti per le installazioni che utilizzano Windows Installer.

 Sebbene sia possibile utilizzare diversi prodotti per creare il programma di installazione VSPackage, in questa discussione si presuppone l'utilizzo dei file di Windows Installer (*MSI).* Quando si crea il programma di installazione, è necessario gestire correttamente la distribuzione dei file in modo che il conteggio dei riferimenti corretto venga eseguito in qualsiasi momento. Di conseguenza, versioni diverse del prodotto non interferiranno o si romperanno a vicenda in una combinazione di scenari di installazione e disinstallazione.

 In Windows Installer, il conteggio dei riferimenti si verifica a livello di componente. È necessario organizzare con attenzione le risorse, ovvero file, voci del Registro di sistema e così via, in componenti. Esistono altri livelli di organizzazione, ad esempio moduli, funzionalità e prodotti, che possono essere utili in scenari diversi. Per ulteriori informazioni, vedere [Nozioni di base su Windows Installer](../../extensibility/internals/windows-installer-basics.md).

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Linee guida per la configurazione della creazione per l'installazione side-by-side

- Creare file e chiavi del Registro di sistema condivisi tra le versioni nei propri componenti.

     In questo modo è possibile consumarli facilmente nella versione successiva. Ad esempio, librerie dei tipi registrate a livello globale, estensioni di file, altri elementi registrati in **HKEY_CLASSES_ROOT**e così via.

- Raggruppare i componenti condivisi in moduli unione separati.

     Questa strategia consente di creare correttamente per l'installazione side-by-side in futuro.

- Installare i file condivisi e le chiavi del Registro di sistema utilizzando gli stessi componenti di Windows Installer tra le versioni.

     Se si utilizza un componente diverso, i file e le voci del Registro di sistema vengono disinstallati quando viene disinstallato un VSPackage con versione con controllo delle versioni, ma un altro VSPackage è ancora installato.

- Non combinare elementi con versione e condivisi nello stesso componente.

     In questo modo è impossibile installare gli elementi condivisi in una posizione globale e gli elementi con controllo delle versioni in posizioni isolate.

- Non dispongono di chiavi del Registro di sistema condivise che puntano a file con versione.

     In caso contrario, le chiavi condivise verranno sovrascritte quando viene installato un altro VSPackage con controllo delle versioni. Dopo aver rimosso la seconda versione, il file a cui punta la chiave non è più presente.

## <a name="see-also"></a>Vedere anche
- [Scegliere tra package VS condivisi e con controllo delle versioni](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Scenari di installazione di VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
