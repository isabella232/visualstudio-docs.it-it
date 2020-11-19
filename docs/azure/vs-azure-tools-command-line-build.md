---
title: Compilazione da riga di comando per Azure | Documentazione Microsoft
description: Compilazione da riga di comando per Azure
author: ghogen
manager: jillfra
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/05/2017
ms.author: ghogen
ms.openlocfilehash: 64c18ea8b572d8481b2b2d04f8a8e16f21afc44a
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902493"
---
# <a name="building-azure-projects-from-the-command-line"></a>Compilazione di progetti Azure dalla riga di comando
Tramite Microsoft Build Engine (MSBuild) è possibile compilare prodotti in ambienti lab di compilazione in cui Visual Studio non è installato. MSBuild usa per i file di progetto il formato XML, che è estendibile e completamente supportato da Microsoft. Usando il formato file MSBuild è possibile indicare quali elementi devono essere compilati per una o più piattaforme o configurazioni.

È anche possibile eseguire MSBuild alla riga dei comandi, come illustrato in questo argomento. Impostando le proprietà nella riga dei comandi, è possibile compilare configurazioni specifiche di un progetto. Analogamente, è possibile definire le destinazioni compilate dal comando di MSBuild. Per altre informazioni sui parametri della riga di comando e su MSBuild, vedere [Riferimenti alla riga di comando di MSBuild](../msbuild/msbuild-command-line-reference.md).

## <a name="msbuild-parameters"></a>Parametri MSBuild
Il modo più semplice per creare un pacchetto consiste nell'eseguire MSBuild con l'opzione `/t:Publish` . Per impostazione predefinita, questo comando crea una directory in relazione alla cartella radice del progetto, ad esempio `<ProjectDirectory>\bin\Configuration\app.publish\`. Quando si compila un progetto Azure, vengono generati due file, il file del pacchetto e il file di configurazione di accompagnamento:

* File del pacchetto (`project.cspkg`)
* File di configurazione(`ServiceConfiguration.TargetProfile.cscfg`)

Per impostazione predefinita, ogni progetto Azure include un file di configurazione del servizio per le compilazioni locali (debug) e un altro per le compilazioni cloud (gestione temporanea o produzione), ma è possibile aggiungere o rimuovere i file di configurazione del servizio in base alle proprie esigenze. Quando si compila un pacchetto all'interno di Visual Studio, viene chiesto quale file di configurazione del servizio includere insieme al pacchetto. Quando si compila un pacchetto usando MSBuild, il file di configurazione del servizio locale viene incluso per impostazione predefinita. Per includere un file di configurazione del servizio diverso, impostare la proprietà `TargetProfile` del comando MSBuild (`MSBuild /t:Publish /p:TargetProfile=ProfileName`).

Se si vuole usare una directory alternativa per i file di configurazione e del pacchetto archiviati, impostare il percorso usando l'opzione `/p:PublishDir=Directory\`, inclusa la barra rovesciata finale.

## <a name="next-steps"></a>Passaggi successivi
Dopo la compilazione, sarà possibile distribuire il pacchetto in Azure.
