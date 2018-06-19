---
title: Come usare kubectl con Connected Environment | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 03/12/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Sviluppo rapido Kubernetes con contenitori e microservizi in Azure
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: douge
ms.openlocfilehash: 138dce09e0d53dc47703b9c6f56a7efda4adc255
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31883527"
---
# <a name="use-kubectl-with-a-connected-environment"></a>Usare `kubectl` con Connected Environment

È possibile accedere al cluster Kubernetes all'interno di un ambiente Connected Environment e usare strumenti esistenti di Kubernetes come `kubectl`.

L'esecuzione di `vsce env create` o `vsce env select` aggiungerà automaticamente un contesto di configurazione `kubectl` per l'utente, quindi kubectl deve essere già connesso al cluster VSCE Kubernetes. Esempi:
- Confermare il contesto corrente: `kubectl config current-context`
- Elencare tutti i contesti disponibili: `kubectl config get-contexts`. Il nome di un cluster Kubernetes creato da VSCE sarà nel formato "vsce -<guid>".
- Modificare il contesto: `kubectl config use-context <context-name>`
- Visualizzare il dashboard di Kubernetes: eseguire `kubectl proxy`, quindi aprire il browser all'indirizzo restituito da questo comando (accodare `/ui` all'URL per passare al dashboard di Kubernetes).
- Elencare i servizi in esecuzione nello spazio VSCE predefinito denominato *mainline*: `kubectl get services --namespace=mainline`

