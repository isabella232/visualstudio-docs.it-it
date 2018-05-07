---
title: 'Procedura: Modificare la directory di output della compilazione | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1e60ed79adf8a7b0ff2f2d66d0773c85398dea8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-change-the-build-output-directory"></a>Procedura: modificare la directory dell'output compilato
Il percorso dell'output generato dal progetto può essere specificato a livello di singole configurazioni (per debug e/o rilascio).  
  
> [!NOTE]
>  Se si ha un progetto **Installazione**, vedere la nota alla fine di questo articolo.  
  
## <a name="change-the-build-output-directory"></a>Modificare la directory di output della compilazione  
  
#### <a name="to-change-the-build-output-directory"></a>Per modificare la directory dell'output di compilazione  
  
1.  Sulla barra dei menu scegliere **Progetto** > **<Appname>Proprietà**. In alternativa, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà**.  
  
2.  Per i progetti Basic, selezionare la scheda **Compilazione** . Per i progetti C#, selezionare la scheda **Compilazione**. Per un progetto C++ o JavaScript, selezionare la scheda **Generale** .  
  
3.  Nell'elenco a discesa della configurazione nella parte superiore, scegliere la configurazione per cui si vuole modificare il percorso di output (debug, rilascio o tutte).  
  
     Individuare la voce relativa al percorso di output (**Percorso dell'output di compilazione** in Visual Basic **Directory di output** in Visual C++, **Percorso di Output** in JavaScript e C#). Specificare una nuova directory dell'output di compilazione relativa alla directory del progetto.  
  
> [!NOTE]
>  In un progetto di installazione, la casella **Nome file di output** modifica solo il percorso del file *Setup.exe* file, non il percorso dei file di progetto. Per altre informazioni, vedere **Compilazione, proprietà di configurazione, finestra di dialogo delle proprietà del progetto di distribuzione**.  
  
## <a name="see-also"></a>Vedere anche  
 [Pagina Compilazione, Creazione progetti (C#)](../ide/reference/build-page-project-designer-csharp.md)   
 [Pagina delle proprietà Generale (Progetto)](/cpp/ide/general-property-page-project)   
 [Compilare](../ide/compiling-and-building-in-visual-studio.md)