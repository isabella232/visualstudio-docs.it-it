---
title: 'CA2212: Non contrassegnare componenti serviti con WebMethod | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 695cf05f1407f7a463f210c920e54148c49b3ef3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847045"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Non contrassegnare componenti serviti con WebMethod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Category|Microsoft.Usage|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo in un tipo che eredita da <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> contrassegnato con <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.Web.Services.WebMethodAttribute> si applica ai metodi all'interno di un servizio Web XML creati mediante ASP.NET. rende il metodo chiamabile dai client Web remoti. Il metodo e la classe deve essere pubblico e in esecuzione in un'applicazione Web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> i tipi sono ospitati da applicazioni COM+ e possono utilizzare servizi COM+. <xref:System.Web.Services.WebMethodAttribute> non viene applicato a <xref:System.EnterpriseServices.ServicedComponent> perché non sono progettati per gli stessi scenari. In particolare, aggiungendo l'attributo per il <xref:System.EnterpriseServices.ServicedComponent> metodo non esegue il metodo chiamabile dai client Web remoti. In quanto <xref:System.Web.Services.WebMethodAttribute> e un <xref:System.EnterpriseServices.ServicedComponent> metodo comportamenti in conflitto e i requisiti per contesto e flusso delle transazioni, il comportamento del metodo sarà corretto in determinati scenari.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere l'attributo di <xref:System.EnterpriseServices.ServicedComponent> (metodo).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Sono presenti scenari in cui la combinazione di questi elementi è corretta.

## <a name="see-also"></a>Vedere anche
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>



