---
title: 'Procedura: Eseguire il debug in modalità mista | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 9939c3eef0c2037e02c23573e246dd12d8934a3c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968515"
---
# <a name="how-to-debug-in-mixed-mode"></a>Procedura: Eseguire il debug in modalità mista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nelle procedure riportate di seguito viene spiegato come eseguire il debug in modalità mista, ovvero sia di codice gestito che di codice nativo. Gli scenari possibili sono due, a seconda che la DLL o l'applicazione sia scritta in codice nativo:  
  
-   L'applicazione che chiama la DLL è scritta in codice nativo. In tal caso, la DLL è gestita ed è necessario attivare sia il debugger del codice gestito sia quello del codice nativo per eseguire il debug di entrambi. Ciò è possibile archiviare il  **\<progetto > pagine delle proprietà** nella finestra di dialogo. L'esecuzione di questa operazione varia a seconda che il debug venga avviato dal progetto della DLL o da quello dell'applicazione chiamante.  
  
-   L'applicazione che chiama la DLL è scritta in codice gestito e la DLL è scritta in codice nativo.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>Per abilitare il debug in modalità mista  
  
1.  Nelle **Esplora soluzioni**, selezionare il progetto.  
  
2.  Scegliere **Pagine delle proprietà** dal menu **Visualizza**.  
  
3.  Nel  **\<progetto > pagine delle proprietà** della finestra, espandere il **le proprietà di configurazione** nodo e quindi selezionare **debug**.  
  
4.  Impostare **Tipo debugger** su **Misto** o **Automatico**.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Eseguire il debug da un progetto DLL](../debugger/how-to-debug-from-a-dll-project.md)
