---
title: 'Procedura: eseguire il Debug in modalità mista | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6ee85e5822d4792046c755c85d699dd6a9a5d26
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737167"
---
# <a name="how-to-debug-in-mixed-mode"></a>Procedura: eseguire il debug in modalità mista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nelle procedure riportate di seguito viene spiegato come eseguire il debug in modalità mista, ovvero sia di codice gestito che di codice nativo. Gli scenari possibili sono due, a seconda che la DLL o l'applicazione sia scritta in codice nativo:  
  
-   L'applicazione che chiama la DLL è scritta in codice nativo. In tal caso, la DLL è gestita ed è necessario attivare il debugger gestito e il debugger nativo. Ciò è possibile archiviare il  **\<progetto > pagine delle proprietà** nella finestra di dialogo. L'esecuzione di questa operazione varia a seconda che il debug venga avviato dal progetto della DLL o da quello dell'applicazione chiamante.  
  
-   L'applicazione che chiama la DLL è scritta in codice gestito e la DLL è scritta in codice nativo.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>Per abilitare il debug in modalità mista  
  
1.  Nelle **Esplora soluzioni**, selezionare il progetto.  
  
2.  Nel **View** menu, fare clic su **pagine delle proprietà**.  
  
3.  Nel  **\<progetto > pagine delle proprietà** della finestra, espandere il **le proprietà di configurazione** nodo e quindi selezionare **debug**.  
  
4.  Impostare **tipo di Debugger** a **misto** oppure **automatico**.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Eseguire il debug da un progetto di DLL](../debugger/how-to-debug-from-a-dll-project.md)



