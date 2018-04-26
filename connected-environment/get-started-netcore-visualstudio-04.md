---
title: 'Creare un ambiente di sviluppo .NET Core con i contenitori usando Kubernetes nel cloud con Visual Studio - Passaggio 4: Eseguire il debug di un contenitore in Kubernetes | Microsoft Docs'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Sviluppo rapido Kubernetes con contenitori e microservizi in Azure
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: douge
ms.openlocfilehash: 75588fcabbba739c4670da42e24665428ff89130
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Introduzione a Connected Environment con .NET Core e Visual Studio

Passaggio precedente: [Creare un ambiente di sviluppo in Azure](get-started-netcore-visualstudio-03.md)

## <a name="debug-a-container-in-kubernetes"></a>Eseguire il debug di un contenitore in Kubernetes
È possibile eseguire il debug dell'applicazione solo dopo il completamento della creazione dell'ambiente di sviluppo. Impostare un punto di interruzione nel codice, ad esempio alla riga 20 nel file `HomeController.cs` in cui viene impostata la variabile `Message`. Premere **F5** per avviare il debug. 

Visual Studio comunicherà con l'ambiente di sviluppo per compilare e distribuire l'applicazione e quindi aprire un browser con l'app Web in esecuzione. Potrebbe sembrare che il contenitore sia in esecuzione in locale, ma in realtà è in esecuzione nell'ambiente di sviluppo in Azure. L'indirizzo localhost viene usato perché Connected Environment crea un tunnel SSH temporaneo per il contenitore in esecuzione in Azure.

Fare clic sul collegamento "**About**" nella parte superiore della pagina per attivare il punto di interruzione. È possibile accedere in modo completo alle informazioni di debug, proprio come se il codice fosse eseguito in locale, ad esempio stack di chiamate, variabili locali, informazioni sulle eccezioni e così via.

> [!div class="nextstepaction"]
> [Chiamare un altro contenitore](get-started-netcore-visualstudio-05.md)