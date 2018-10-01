---
title: 'Procedura: Modificare la directory di output della compilazione | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a12accc247d79a68eaafc9878dc5e9d7d8c7d6dc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530776"
---
# <a name="how-to-change-the-build-output-directory"></a>Procedura: modificare la directory dell'output compilato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: modificare la Directory di Output di compilazione](https://docs.microsoft.com/visualstudio/ide/how-to-change-the-build-output-directory).  
  
Il percorso dell'output generato dal progetto può essere specificato a livello di singole configurazioni (per debug e/o rilascio).  
  
> [!NOTE]
>  Se si ha un progetto **Installazione** , vedere la nota alla fine di questo articolo.  
  
## <a name="changing-the-build-output-directory"></a>Modifica della directory dell'output di compilazione  
  
#### <a name="to-change-the-build-output-directory"></a>Per modificare la directory dell'output di compilazione  
  
1.  Nella barra dei menu scegliere **Progetto**, *NomeApp* **Proprietà**. In alternativa, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà**.  
  
2.  Per i progetti Basic, selezionare la scheda **Compilazione** . Per i progetti Visual C#, selezionare la scheda **Compilazione** . Per un progetto C++ o JavaScript, selezionare la scheda **Generale** .  
  
3.  Nell'elenco a discesa della configurazione nella parte superiore, scegliere la configurazione per cui si vuole modificare il percorso di output (debug, rilascio o tutte).  
  
     Individuare la voce relativa al percorso di output (**Percorso dell'output di compilazione** in Visual Basic **Directory di output** in Visual C++, **Percorso di Output** in JavaScript e C#). Specificare una nuova directory dell'output di compilazione relativa alla directory del progetto.  
  
> [!NOTE]
>  In un progetto di installazione, la casella **Nome file di output** modifica solo il percorso del file Setup.exe file, non il percorso dei file di progetto. Per ulteriori informazioni, vedere **Compilazione, proprietà di configurazione, finestra di dialogo delle proprietà del progetto di distribuzione**.  
  
## <a name="see-also"></a>Vedere anche  
 [Build Page, Project Designer (C#)](../ide/reference/build-page-project-designer-csharp.md)  (Pagina Compilazione, Progettazione progetti (C#))  
 [General Property Page (Project)](http://msdn.microsoft.com/library/593b383c-cd0f-4dcd-ad65-9ec9b4b19c45)  (Pagina delle proprietà Generale (Progetto))  
 [Compiling and Building](../ide/compiling-and-building-in-visual-studio.md) (Compilazione e creazione)



