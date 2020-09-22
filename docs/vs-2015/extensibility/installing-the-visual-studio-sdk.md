---
title: Installazione di Visual Studio SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: visual-studio-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88a6266a3f5910def0bf5041a37f89c2b3d67416
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840326"
---
# <a name="installing-the-visual-studio-sdk"></a>Installazione di Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installazione di Visual Studio SDK come parte di un'installazione di Visual Studio  
 Se si vuole includere VSSDK nell'installazione di Visual Studio, è necessario eseguire un'installazione personalizzata.  
  
> [!NOTE]
> Nel file eseguibile di installazione, Visual Studio SDK è denominato **Visual Studio Extensibility Tools**.  
  
1. Avviare l'installazione di Visual Studio 2015. È possibile installare qualsiasi edizione di Visual Studio eccetto Express.  
  
2. Nella prima schermata selezionare **personalizzato**, non **predefinito**. Fare clic su **Avanti**.  
  
3. Verrà visualizzata una visualizzazione albero delle funzionalità personalizzate. Aprire **strumenti comuni**. Dovrebbe essere visualizzato **Visual Studio Extensibility Tools** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4. Controllare **Visual Studio Extensibility Tools** , quindi fare clic su **Avanti** e continuare l'installazione.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Installazione di Visual Studio SDK dopo l'installazione di Visual Studio  
 Se si decide di installare Visual Studio SDK dopo aver completato l'installazione di Visual Studio, attenersi alla procedura seguente:  
  
1. Passare a **Pannello di controllo/programmi/programmi e funzionalità**e cercare **Visual Studio 2015**. È possibile installare Visual Studio SDK per qualsiasi edizione di Visual Studio 2015 eccetto Express.  
  
2. Fare clic con il pulsante destro del mouse su **Visual Studio 2015**, quindi scegliere **Cambia**. Verrà visualizzata la pagina installazione.  
  
3. Seguire la stessa procedura descritta in **installazione di Visual Studio SDK come parte di un'installazione di Visual Studio** .  
  
4. Fare clic sul collegamento **Visual Studio Extensibility Tools** per installare Visual Studio SDK.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Installazione di Visual Studio SDK da una soluzione  
 Se si apre una soluzione con un progetto di estendibilità senza prima installare il VSSDK, verrà visualizzata una barra informazioni evidenziata sopra la Esplora soluzioni. Il comando dovrebbe essere simile al seguente:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Installazione di Visual Studio SDK dalla riga di comando  
 È possibile installare VSSDK dalla riga di comando usando l'opzione **/InstallSelectableItems** con il programma di installazione di Visual Studio. Per informazioni dettagliate sull'uso dei parametri della riga di comando con il programma di installazione, vedere [installazione di Visual Studio 2015](../install/install-visual-studio-2015.md).  
  
 Ecco come installare VSSDK in modo invisibile all'utente usando il programma di installazione della community di Visual Studio 2015:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Si noti che è necessario usare il programma di installazione di Visual Studio che corrisponde alla versione installata di Visual Studio. Ad esempio, se nel computer è installato Visual Studio Enterprise, è necessario eseguire il programma di installazione di Visual Studio Enterprise (vs_enterprise.exe).
