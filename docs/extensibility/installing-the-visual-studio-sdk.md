---
title: Installazione di Visual Studio SDK Documenti Microsoft
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f391708abbd8a9b66f2dfd5aaa6559cb075910d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710352"
---
# <a name="install-the-visual-studio-sdk"></a>Installare Visual Studio SDK

Visual Studio SDK (Software Development Kit) è una funzionalità facoltativa nel programma di installazione di Visual Studio.The Visual Studio SDK (Software Development Kit) is an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installare Visual Studio SDK come parte di un'installazione di Visual StudioInstall the Visual Studio SDK as part of a Visual Studio installation

Per includere Visual Studio NELL'installazione di Visual Studio, installare il carico di lavoro di sviluppo delle **estensioni** di Visual Studio in **Altri set di strumenti**. Questo carico di lavoro installerà Visual Studio SDK e i prerequisiti necessari. È possibile ottimizzare ulteriormente l'installazione selezionando o deselezionando i componenti dalla visualizzazione **Riepilogo.**

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Installare Visual Studio SDK dopo l'installazione di Visual StudioInstall the Visual Studio SDK after installing Visual Studio

Per installare Visual Studio SDK dopo aver completato l'installazione di Visual Studio, eseguire nuovamente il programma di installazione di Visual Studio e selezionare il carico di lavoro di **sviluppo dell'estensione** di Visual Studio.To install the Visual Studio SDK after completing your Visual Studio installation, rerun the Visual Studio installer and select the Visual Studio extension development workload.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Installare Visual Studio SDK da una soluzioneInstall the Visual Studio SDK from a solution

Se si apre una soluzione con un progetto di estendibilità senza prima installare l'SDK di Visual Studio, verrà visualizzata una finestra di dialogo **Installa funzionalità mancante** per installare il carico di lavoro di **sviluppo dell'estensione** di Visual Studio:If you open a solution with an extensibility project without first installing the VS SDK, you will be prompted by an Install Missing Feature dialog to install the Visual Studio extension development workload:

![Installare lo sviluppo delle estensioniInstall extension development](../extensibility/media/install-extension-development.png "Installare lo sviluppo delle estensioniInstall extension development")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Installare Visual Studio SDK dalla riga di comando

Come con qualsiasi carico di lavoro o componente di Visual Studio, è anche possibile installare il carico di lavoro di **sviluppo dell'estensione** di Visual Studio (ID: Microsoft.VisualStudio.Workload.VisualStudioExtension) dalla riga di comando. Vedere Usare i [parametri della riga di comando per installare Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) per informazioni dettagliate sulle opzioni della riga di comando appropriate e istruzioni generali su come determinare il carico di lavoro o gli identificatori dei componenti.

Si noti che è necessario utilizzare il programma di installazione di Visual Studio che corrisponde alla versione installata di Visual Studio. Ad esempio, se nel computer è installato Visual Studio Enterprise, è necessario eseguire il programma di installazione di Visual Studio Enterprise (*vs_enterprise.exe*).
