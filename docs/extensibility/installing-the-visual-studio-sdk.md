---
title: Installazione di Visual Studio SDK | Microsoft Docs
description: Informazioni sulle opzioni di installazione di Visual Studio Software Development Kit, incluso durante l'installazione di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 331a219210c990aed2f9601cd1f9b1f0bc5710ed
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079163"
---
# <a name="install-the-visual-studio-sdk"></a>Installare Visual Studio SDK

Visual Studio SDK (Software Development Kit) è una funzionalità facoltativa del programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installare Visual Studio SDK come parte di un'installazione di Visual Studio

Per includere VS SDK nell'installazione di Visual Studio, installare il carico di lavoro **sviluppo di estensioni di Visual Studio** in **altri set di strumenti**. Questo carico di lavoro installerà Visual Studio SDK e i prerequisiti necessari. È possibile ottimizzare ulteriormente l'installazione selezionando o deselezionando i componenti dalla visualizzazione **Riepilogo** .

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Installare Visual Studio SDK dopo l'installazione di Visual Studio

Per installare Visual Studio SDK dopo aver completato l'installazione di Visual Studio, eseguire di nuovo il programma di installazione di Visual Studio e selezionare il carico di lavoro **sviluppo di estensioni di Visual Studio** .

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Installare Visual Studio SDK da una soluzione

Se si apre una soluzione con un progetto di estendibilità senza installare prima SDK di Visual Studio, verrà visualizzata una finestra di dialogo **installa funzionalità mancante** per installare il carico di lavoro **sviluppo di estensioni di Visual Studio** :

![Sviluppo di estensioni di installazione](../extensibility/media/install-extension-development.png "Sviluppo di estensioni di installazione")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Installare Visual Studio SDK dalla riga di comando

Come per qualsiasi carico di lavoro o componente di Visual Studio, è anche possibile installare il carico di lavoro **sviluppo di estensioni di Visual Studio** (ID: Microsoft. VisualStudio. workload. VisualStudioExtension) dalla riga di comando. Vedere [usare i parametri della riga di comando per installare Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) per informazioni dettagliate sulle opzioni della riga di comando appropriate e istruzioni generali su come determinare gli identificatori dei carichi di lavoro o dei componenti.

Si noti che è necessario usare il programma di installazione di Visual Studio che corrisponde alla versione installata di Visual Studio. Ad esempio, se nel computer è installato Visual Studio Enterprise, è necessario eseguire il programma di installazione di Visual Studio Enterprise (*vs_enterprise.exe*).
