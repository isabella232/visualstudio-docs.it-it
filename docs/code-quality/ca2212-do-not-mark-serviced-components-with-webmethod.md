---
title: 'CA2212: Non contrassegnare componenti serviti con WebMethod'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 88708fdcb41a43d3e8b3f78b4e66decb7211a4b4
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177422"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Non contrassegnare componenti serviti con WebMethod

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Category|Microsoft.Usage|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un metodo in un tipo che eredita da <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> contrassegnato con <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola

<xref:System.Web.Services.WebMethodAttribute> si applica ai metodi all'interno di un servizio web XML creati mediante ASP.NET. rende il metodo chiamabile dai client web remoti. Il metodo e la classe deve essere pubblico e in esecuzione in un'applicazione web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> i tipi sono ospitati da applicazioni COM+ e possono utilizzare servizi COM+. <xref:System.Web.Services.WebMethodAttribute> non viene applicato a <xref:System.EnterpriseServices.ServicedComponent> perché non sono progettati per gli stessi scenari. In particolare, aggiungendo l'attributo per il <xref:System.EnterpriseServices.ServicedComponent> metodo non esegue il metodo chiamabile dai client web remoti. In quanto <xref:System.Web.Services.WebMethodAttribute> e un <xref:System.EnterpriseServices.ServicedComponent> metodo comportamenti in conflitto e i requisiti per contesto e flusso delle transazioni, il comportamento del metodo sarà corretto in determinati scenari.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rimuovere l'attributo di <xref:System.EnterpriseServices.ServicedComponent> (metodo).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi

Non escludere un avviso da questa regola. Sono presenti scenari in cui la combinazione di questi elementi è corretta.

## <a name="see-also"></a>Vedere anche

- <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>
- <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>