---
title: Gestione dei componenti | Microsoft Docs
description: Informazioni su come gestire i componenti Windows installer durante la creazione di un programma di installazione VSPackage in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6ff094b0ad7457eabc569ce10d44a80c1f6db639cc7c855dc4f27c77c68edbc4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121275528"
---
# <a name="component-management"></a>Gestione dei componenti
Le unità di attività nel programma di Windows installer sono denominate componenti Windows Installer (talvolta denominati WIC o semplicemente componenti). Un GUID identifica ogni WIC, ovvero l'unità di base di installazione e conteggio dei riferimenti per le installazioni che usano Windows programma di installazione.

 Anche se è possibile usare diversi prodotti per creare il programma di installazione di VSPackage, questa discussione presuppone l'uso di file di Windows Installer *(.msi*). Quando si crea il programma di installazione, è necessario gestire correttamente la distribuzione dei file in modo che il conteggio dei riferimenti sia sempre corretto. Di conseguenza, versioni diverse del prodotto non interferiranno tra loro o si interromperanno a vicenda in una combinazione di scenari di installazione e disinstallazione.

 Nel Windows di installazione, il conteggio dei riferimenti viene eseguito a livello di componente. È necessario organizzare attentamente le risorse, ovvero file, voci del Registro di sistema e così via, in componenti. Esistono altri livelli di organizzazione, ad esempio moduli, funzionalità e prodotti, che possono essere utili in scenari diversi. Per altre informazioni, vedere [nozioni di Windows installer.](../../extensibility/internals/windows-installer-basics.md)

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Linee guida per la creazione della configurazione per l'installazione side-by-side

- Creare file e chiavi del Registro di sistema condivisi tra le versioni nei propri componenti.

     In questo modo è possibile utilizzare facilmente questi dati nella versione successiva. Ad esempio, librerie dei tipi registrate a livello globale, estensioni di file, altri elementi registrati in **HKEY_CLASSES_ROOT** e così via.

- Raggruppare i componenti condivisi in moduli unione separati.

     Questa strategia consente di creare correttamente l'installazione side-by-side in futuro.

- Installare i file condivisi e le chiavi del Registro di sistema usando gli stessi componenti Windows installer tra versioni diverse.

     Se si usa un componente diverso, i file e le voci del Registro di sistema vengono disinstallati quando un VSPackage con versione viene disinstallato ma è ancora installato un altro VSPackage.

- Non combinare elementi condivisi e con controllo delle versioni nello stesso componente.

     In questo modo non è possibile installare gli elementi condivisi in una posizione globale e gli elementi con controllo delle versioni in posizioni isolate.

- Non sono state condivise chiavi del Registro di sistema che puntano a file con versione.

     In questo caso, le chiavi condivise verranno sovrascritte quando viene installato un altro VSPackage con controllo delle versioni. Dopo aver rimosso la seconda versione, il file a cui punta la chiave non è più disponibile.

## <a name="see-also"></a>Vedi anche
- [Scegliere tra pacchetti VSPackage condivisi e con versione](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Scenari di installazione di VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
