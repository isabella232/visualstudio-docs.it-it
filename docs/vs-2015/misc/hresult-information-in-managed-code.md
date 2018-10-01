---
title: Informazioni su HRESULT nel codice gestito | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, HRESULT information
- HRESULT, managed VSPackages
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
manager: douge
ms.openlocfilehash: c87fc618f1c80b60bbd2f95537dc70a83eb2bdc7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517664"
---
# <a name="hresult-information-in-managed-code"></a>Informazioni su HRESULT nel codice gestito
L'interazione tra codice gestito e COM può causare problemi in presenza di valori restituiti HRESULT.  
  
 In un'interfaccia COM un valore restituito HRESULT può avere le funzioni seguenti:  
  
-   Fornire informazioni sugli errori (ad esempio, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>).  
  
-   Fornire informazioni sullo stato in relazione al normale comportamento del programma.  
  
 Quando COM esegue una chiamata nel codice gestito, i valori HRESULT possono causare questi problemi:  
  
-   Le funzioni COM che restituiscono valori HRESULT minori di zero (codici di errore) generano eccezioni.  
  
-   I metodi COM che restituiscono regolarmente due o più codici di riuscita diversi, ad esempio, <xref:Microsoft.VisualStudio.VSConstants.S_OK> o <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>, non possono essere distinti.  
  
 Poiché molte delle [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] funzioni COM restituiscono valori HRESULT minori di zero o restituiscono codici di riuscita diversi, il [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] gli assembly di interoperabilità sono stati scritti in modo che vengano mantenute le firme del metodo. Tutti i [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] metodi di interoperabilità sono di `int` tipo. I valori HRESULT vengono passati attraverso il livello di interoperabilità senza modifica e senza generare eccezioni.  
  
 Poiché una funzione COM restituisce un valore HRESULT al metodo gestito che la chiama, il metodo chiamante deve controllare il valore HRESULT e generare eccezioni, se necessario.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Gestione di valori HRESULT restituiti al codice gestito da COM  
 Quando si chiama un'interfaccia COM dal codice gestito, esaminare il valore HRESULT e generare un'eccezione, se necessario. Il <xref:Microsoft.VisualStudio.ErrorHandler> classe contiene il <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> metodo, che genera un'eccezione COM, in base al valore HRESULT passato ad esso.  
  
 Per impostazione predefinita, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> genera un'eccezione ogni volta che viene passato un HRESULT che ha un valore minore di zero. Nei casi in cui tali valori HRESULT sono valori accettabili e deve essere generata alcuna eccezione, i valori HRESULT aggiuntivi devono essere passati a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> dopo che i valori vengono testati. Se il valore HRESULT testato corrisponde a qualsiasi valore HRESULT passati in modo esplicito <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, viene generata alcuna eccezione.  
  
> [!NOTE]
>  Il <xref:Microsoft.VisualStudio.VSConstants> classe contiene costanti per valori HRESULT comuni, ad esempio, <xref:Microsoft.VisualStudio.VSConstants.S_OK> e <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, e [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] HRESULT, ad esempio <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> e <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> fornisce anche il <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> e <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> metodi, che corrispondono alle macro SUCCEEDED e FAILED in COM.  
  
 Ad esempio, si consideri la seguente chiamata di funzione, in cui <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> è un valore restituito accettabile, ma qualsiasi altro valore HRESULT minore di zero rappresenta un errore.  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 Se è presenti più valori restituiti accettabili, sono sufficiente aggiungere ulteriori valori HRESULT all'elenco nella chiamata a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Restituzione di valori HRESULT a COM dal codice gestito  
 Se si verifica alcuna eccezione, il codice gestito restituisce <xref:Microsoft.VisualStudio.VSConstants.S_OK> alla funzione COM che lo ha chiamato. L'interoperabilità COM supporta eccezioni comuni fortemente tipizzate nel codice gestito. Ad esempio, un metodo che riceve un inaccettabili `null` argomento genera un <xref:System.ArgumentNullException>.  
  
 Se non si è sicuri quale eccezione generare, ma si conosce il valore HRESULT si vuole restituire a COM, è possibile usare il <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> metodo per generare un'eccezione appropriata. Ciò funziona anche con un errore non standard, ad esempio, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> tenta di eseguire il mapping di HRESULT passato a un'eccezione fortemente tipizzata. Se ciò non è possibile, genera un'eccezione COM generica. Il risultato finale è che il valore HRESULT passato a <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> dal codice gestito viene restituito alla funzione COM che lo ha chiamato.  
  
> [!NOTE]
>  Le eccezioni compromettono le prestazioni e servono per indicare condizioni anomale dei programmi. Le condizioni che si verificano spesso devono essere gestite inline, invece di generare un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [VSPackage gestiti](../misc/managed-vspackages.md)   
 [Interoperabilità con codice non gestito](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [Procedura: eseguire il mapping di HRESULT ed eccezioni](http://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [Compilazione di componenti COM per l'interoperabilità](http://msdn.microsoft.com/en-us/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [VSPackage gestiti](../misc/managed-vspackages.md)