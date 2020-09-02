---
title: Creazione di un'estensione con una finestra degli strumenti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 94c8335b8d723ef20c04cfffe6b3788d71ecaa4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431849"
---
# <a name="creating-an-extension-with-a-tool-window"></a>Creazione di un'estensione con una finestra degli strumenti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa procedura illustra come usare il modello di progetto VSIX e il modello di elemento della **finestra degli strumenti personalizzata** per creare un'estensione con una finestra degli strumenti.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Creazione di una finestra degli strumenti  
  
1. Creare un progetto VSIX denominato **FirstWindow**. Il modello di progetto VSIX è reperibile nella finestra di dialogo **nuovo progetto** in **Visual C#/extensibility**.  
  
2. Quando si apre il progetto, aggiungere un modello di elemento della finestra degli strumenti denominato **FirstWindow**. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi/nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a **Visual C#/extensibility** e selezionare **finestra degli strumenti personalizzata**. Nel campo **nome** nella parte inferiore della finestra modificare il nome del file della finestra degli strumenti in **FirstWindow.cs**.  
  
3. Compilare il progetto e avviare il debug.  
  
     Viene visualizzata l'istanza sperimentale di Visual Studio. Per ulteriori informazioni sull'istanza sperimentale, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
4. Nell'istanza sperimentale, passare a **Visualizza/altre finestre**.  
  
     Verrà visualizzata una voce di menu per **FirstWindow**. quindi farvi clic.  
  
     Dovrebbe essere visualizzata una finestra degli strumenti con il titolo **FirstWindow** e un pulsante che dice **clic su me!.**
