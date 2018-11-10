---
title: Compilazione dalla riga di comando di Azure | Microsoft Docs
description: Compilazione dalla riga di comando di Azure
author: ghogen
manager: douge
assetId: 94b35d0d-0d35-48b6-b48b-3641377867fd
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/05/2017
ms.author: ghogen
ms.openlocfilehash: fce752d91ebaa765e18efef117a3b6efe750119c
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002940"
---
# <a name="building-azure-projects-from-the-command-line"></a>Compilazione di progetti Azure dalla riga di comando
Usa Microsoft Build Engine (MSBuild), è possibile compilare prodotti in ambienti di laboratorio di compilazione in cui non è installato Visual Studio. MSBuild Usa un formato XML per i file di progetto che è estendibile e completamente supportata da Microsoft. Usa il formato file MSBuild, è possibile descrivere quali elementi devono essere compilati per uno o più piattaforme e configurazioni.

È anche possibile eseguire MSBuild dalla riga di comando e illustrato in questo argomento. Impostando le proprietà nella riga di comando, è possibile compilare configurazioni specifiche di un progetto. Analogamente, è possibile definire le destinazioni di MSBuild compila. Per altre informazioni sui parametri della riga di comando e su MSBuild, vedere [riferimenti alla riga di comando di MSBuild](https://msdn.microsoft.com/library/ms164311.aspx).

## <a name="msbuild-parameters"></a>Parametri MSBuild
Il modo più semplice per creare un pacchetto consiste nell'eseguire MSBuild con il `/t:Publish` opzione. Per impostazione predefinita, questo comando crea una directory in relazione alla cartella radice del progetto, ad esempio `<ProjectDirectory>\bin\Configuration\app.publish\`. Quando si compila un progetto Azure, vengono generati due file: il file del pacchetto stesso e il relativo file di configurazione:

* File del pacchetto (`project.cspkg`)
* File di configurazione (`ServiceConfiguration.TargetProfile.cscfg`)

Per impostazione predefinita, ogni progetto Azure include un file di configurazione del servizio per compilazioni locali (debug) e un altro per le compilazioni cloud (gestione temporanea o produzione). Tuttavia, è possibile aggiungere o rimuovere i file di configurazione del servizio in base alle esigenze. Quando si compila un pacchetto all'interno di Visual Studio, viene chiesto quale file di configurazione del servizio includere insieme al pacchetto. Quando si compila un pacchetto usando MSBuild, il file di configurazione del servizio locale è incluso per impostazione predefinita. Per includere un file di configurazione del servizio diverso, impostare il `TargetProfile` proprietà del comando MSBuild (`MSBuild /t:Publish /p:TargetProfile=ProfileName`).

Se si desidera usare una directory alternativa per il file di configurazione e del pacchetto archiviati, impostare il percorso usando il `/p:PublishDir=Directory\` opzione, che include il separatore barra rovesciata finale.

## <a name="next-steps"></a>Passaggi successivi
Dopo che il pacchetto viene compilato, è possibile distribuirla in Azure.