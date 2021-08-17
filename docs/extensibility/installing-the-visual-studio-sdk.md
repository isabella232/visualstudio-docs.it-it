---
title: Installazione del Visual Studio SDK | Microsoft Docs
description: Informazioni sulle opzioni per installare Visual Studio Software Development Kit, anche durante l Visual Studio installazione.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1f0aeff420a5a043a6f6a9fd3dbfbf4c5975eba1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122070230"
---
# <a name="install-the-visual-studio-sdk"></a>Installare Visual Studio SDK

L Visual Studio SDK (Software Development Kit) è una funzionalità facoltativa di Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installare l'SDK Visual Studio come parte di un'Visual Studio installazione

Per includere VS SDK nell'installazione Visual Studio, installare il carico di **lavoro** Visual Studio sviluppo di estensioni in **Altri set di strumenti**. Questo carico di lavoro installerà Visual Studio SDK e i prerequisiti necessari. È possibile ottimizzare ulteriormente l'installazione selezionando o deselezionando i componenti dalla **visualizzazione** Riepilogo.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Installare l'SDK Visual Studio dopo l'installazione Visual Studio

Per installare l'SDK Visual Studio dopo aver completato l'installazione Visual Studio, eseguire di nuovo  il programma di installazione Visual Studio e selezionare il carico Visual Studio di sviluppo dell'estensione.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Installare l Visual Studio SDK da una soluzione

Se si apre una soluzione con un progetto di estendibilità senza prima  installare VS SDK, verrà visualizzata una finestra di dialogo Installa funzionalità mancante per installare il carico di lavoro di sviluppo dell'estensione **Visual Studio:**

![Installare lo sviluppo di estensioni](../extensibility/media/install-extension-development.png "Installare lo sviluppo di estensioni")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Installare l Visual Studio SDK dalla riga di comando

Come per qualsiasi Visual Studio carico di lavoro o componente, è anche possibile installare il carico di lavoro di sviluppo dell'estensione **Visual Studio** (ID: Microsoft.VisualStudio.Workload.VisualStudioExtension) dalla riga di comando. Vedere [Usare i parametri della riga di](../install/use-command-line-parameters-to-install-visual-studio.md) comando per installare Visual Studio per informazioni dettagliate sulle opzioni della riga di comando appropriate e istruzioni generali su come determinare gli identificatori del carico di lavoro o del componente.

Si noti che è necessario usare il Visual Studio che corrisponde alla versione installata di Visual Studio. Ad esempio, se nel computer Visual Studio Enterprise installato, è necessario eseguire il programma di Visual Studio Enterprise (*vs_enterprise.exe*).
