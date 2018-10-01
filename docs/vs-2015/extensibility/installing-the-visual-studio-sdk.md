---
title: Installazione di Visual Studio SDK | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- visual-studio-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1bbf029fb27e54b68fe6bef36d0c3f2f7329c45b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528702"
---
# <a name="installing-the-visual-studio-sdk"></a>Installazione di Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installazione di Visual Studio SDK come parte di un'installazione di Visual Studio  
 Se si desidera includere VSSDK nell'installazione di Visual Studio, è necessario eseguire un'installazione personalizzata.  
  
> [!NOTE]
>  Nel file eseguibile di installazione, viene chiamato in Visual Studio SDK **Visual Studio Extensibility Tools**.  
  
1.  Avviare l'installazione di Visual Studio 2015. È possibile installare qualsiasi edizione di Visual Studio, ad eccezione di Express.  
  
2.  Nella prima schermata, selezionare **Custom**, non **predefinito**. Scegliere **Avanti**.  
  
3.  Si deve ottenere una visualizzazione albero delle funzionalità personalizzate. Aprire **strumenti comuni**. Si noterà **Visual Studio Extensibility Tools** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4.  Controllare **Visual Studio Extensibility Tools** , quindi fare clic su **successivo** e continuare l'installazione.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Installazione di Visual Studio SDK dopo l'installazione di Visual Studio  
 Se si decide di installare Visual Studio SDK dopo aver completato l'installazione di Visual Studio, è necessario seguire la procedura seguente:  
  
1.  Passare a **Pannello di controllo / programmi o programmi e funzionalità**e cercare **Visual Studio 2015**. È possibile installare Visual Studio SDK per qualsiasi edizione di Visual Studio 2015, ad eccezione di Express.  
  
2.  Fare doppio clic su **Visual Studio 2015**, quindi fare clic su **modifica**. Verrà visualizzata la pagina di installazione.  
  
3.  Seguire la stessa procedura descritta in **installazione di Visual Studio SDK come parte di un'installazione di Visual Studio** sopra.  
  
4.  Scegliere il **Visual Studio Extensibility Tools** collegamento per installare Visual Studio SDK.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Installazione di Visual Studio SDK da una soluzione  
 Se si apre una soluzione con un progetto di estensibilità senza prima aver installato il SDK di pagina, verrà richiesto da una barra informazioni evidenziato sopra Esplora soluzioni. Dovrebbe essere simile al seguente:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Installazione di Visual Studio SDK dalla riga di comando  
 È possibile installare VSSDK dalla riga di comando usando il **/InstallSelectableItems** passare con il programma di installazione di Visual Studio. Per informazioni dettagliate sull'utilizzo dei parametri della riga di comando con il programma di installazione, vedere [installazione di Visual Studio 2015](../install/install-visual-studio-2015.md).  
  
 Di seguito viene illustrato come installare VSSDK invisibile all'utente tramite il programma di installazione di Visual Studio 2015 Community:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Si noti che è necessario usare il programma di installazione di Visual Studio che corrisponde alla versione installata di Visual Studio. Ad esempio, se hai installato nel computer Visual Studio Enterprise, è necessario eseguire il programma di installazione di Visual Studio Enterprise (vs_enterprise.exe).







