---
title: Installazione di Visual Studio SDK | Microsoft Docs
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4208c20cc3e7da34efaf98af16f0f41d54613824
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340750"
---
# <a name="install-the-visual-studio-sdk"></a>Installare Visual Studio SDK

Visual Studio SDK (Software Development Kit) è una funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installare Visual Studio SDK come parte di un'installazione di Visual Studio

Per includere il SDK di Visual Studio nell'installazione di Visual Studio, installare il **sviluppo di estensioni di Visual Studio** carico di lavoro nella **altri set di strumenti**. Questo carico di lavoro verrà installato Visual Studio SDK e i prerequisiti necessari. È possibile ottimizzare ulteriormente l'installazione selezionando o deselezionando i componenti dal **riepilogo** visualizzazione.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Installare Visual Studio SDK dopo l'installazione di Visual Studio

Per installare Visual Studio SDK dopo aver completato l'installazione di Visual Studio, eseguire nuovamente il programma di installazione di Visual Studio e selezionare il **sviluppo di estensioni di Visual Studio** carico di lavoro.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Installare Visual Studio SDK da una soluzione

Se si apre una soluzione con un progetto di estensibilità senza prima aver installato il SDK di Visual Studio, verrà richiesto da un **installa funzionalità mancanti** finestra di dialogo per installare il **sviluppo di estensioni di Visual Studio** carico di lavoro:

![Installare lo sviluppo di estensioni](../extensibility/media/install-extension-development.png "installare lo sviluppo di estensioni")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Installare Visual Studio SDK dalla riga di comando

Come con qualsiasi carico di lavoro di Visual Studio o un componente, è anche possibile installare il **sviluppo di estensioni di Visual Studio** carico di lavoro (ID: Microsoft.VisualStudio.Workload.VisualStudioExtension) dalla riga di comando. Visualizzare [usare i parametri della riga di comando per installare Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) per informazioni dettagliate sulle opzioni appropriate della riga di comando e istruzioni generali su come determinare gli identificatori del carico di lavoro o componente.

Si noti che è necessario usare il programma di installazione di Visual Studio che corrisponde alla versione installata di Visual Studio. Ad esempio, se hai installato nel computer Visual Studio Enterprise, è necessario eseguire il programma di installazione di Visual Studio Enterprise (*vs_enterprise.exe*).