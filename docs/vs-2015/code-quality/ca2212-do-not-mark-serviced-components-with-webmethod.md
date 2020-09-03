---
title: 'CA2212: non contrassegnare i componenti serviti con WebMethod | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a3c707fef5562b932b6232300131f6e6e6efef6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534563"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Non contrassegnare componenti serviti con WebMethod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Category|Microsoft. Usage|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo in un tipo che eredita da <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> è contrassegnato con <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName> .

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.Web.Services.WebMethodAttribute> si applica ai metodi all'interno di un servizio Web XML che sono stati creati tramite ASP.NET; rende il metodo chiamabile dai client Web remoti. Il metodo e la classe devono essere pubblici ed essere eseguiti in un'applicazione Web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> i tipi sono ospitati da applicazioni COM+ e possono utilizzare i servizi COM+. <xref:System.Web.Services.WebMethodAttribute> non viene applicato ai <xref:System.EnterpriseServices.ServicedComponent> tipi perché non sono destinati agli stessi scenari. In particolare, l'aggiunta dell'attributo al <xref:System.EnterpriseServices.ServicedComponent> metodo non rende il metodo chiamabile dai client Web remoti. Poiché <xref:System.Web.Services.WebMethodAttribute> e un <xref:System.EnterpriseServices.ServicedComponent> Metodo presentano comportamenti e requisiti in conflitto per il contesto e il flusso delle transazioni, il comportamento del metodo non sarà corretto in alcuni scenari.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere l'attributo dal <xref:System.EnterpriseServices.ServicedComponent> metodo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Non esistono scenari in cui la combinazione di questi elementi è corretta.

## <a name="see-also"></a>Vedere anche
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
