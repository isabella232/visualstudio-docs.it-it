---
title: Considerazioni sulla sicurezza durante l'utilizzo di dati XML
description: Informazioni sulle considerazioni sulla sicurezza quando si lavora con i dati XML nell'editor XML o nel debugger XSLT.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 1860fa79502701a0adaa233302d99092c7724dde
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037733"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Considerazioni sulla sicurezza quando si lavora con i dati XML

In questo argomento vengono illustrati i problemi di sicurezza che è necessario conoscere quando si utilizza l'editor XML o il debugger XSLT.

## <a name="xml-editor"></a>Editor XML

L'editor XML è basato sul Visual Studio editor di testo. e si basa sulle classi <xref:System.Xml> e <xref:System.Xml.Xsl> per gestire gran parte dei processi XML.

- Le trasformazioni XSLT vengono eseguite in un nuovo dominio applicazione. Le trasformazioni XSLT sono in *modalità sandbox.* in altri casi, i criteri di sicurezza dall'accesso di codice del computer vengono usati per determinare le autorizzazioni limitate in base alla posizione del foglio di stile XSLT. Ad esempio, per i fogli di stile provenienti da un'area Internet vengono applicate autorizzazioni con la limitazione massima, mentre per i fogli di stile copiati sull'unità disco rigido del computer vengono eseguiti con un livello di Attendibilità totale.

- La classe <xref:System.Xml.Xsl.XslCompiledTransform> viene usata per compilare il codice XSLT in Microsoft Intermediate Language per ottenere prestazioni più veloci durante l'esecuzione.

- Gli schemi che puntano a un percorso esterno nel file di catalogo vengono scaricati automaticamente al primo caricamento dell'editor XML. La classe <xref:System.Xml.Schema.XmlSchemaSet> è usata per compilare gli schemi. Il file di catalogo fornito con l'editor XML non include collegamenti ad schemi esterni. L'utente deve aggiungere in modo esplicito un riferimento allo schema esterno prima che l'editor XML scarica il file di schema. Il download HTTP può essere disabilitato tramite la pagina Opzioni varie **degli** strumenti per l'editor XML.

- L'editor XML usa <xref:System.Net> le classi per scaricare gli schemi

## <a name="xslt-debugger"></a>debugger XSLT

Il debugger XSLT usa il motore di debug gestito di Visual Studio e le classi degli spazi dei nomi <xref:System.Xml> e <xref:System.Xml.Xsl>.

- Il debugger XSLT esegue ogni trasformazione XSLT in un dominio applicazione sandboxed. I criteri di sicurezza dall'accesso di codice del computer vengono usati per determinare le autorizzazioni limitate basate sulla posizione del foglio di stile XSLT. Ad esempio, per i fogli di stile provenienti da un'area Internet vengono applicate autorizzazioni con la limitazione massima, mentre per i fogli di stile copiati sull'unità disco rigido del computer vengono eseguiti con un livello di Attendibilità totale.

- Il foglio di stile XSLT viene compilato usando la classe <xref:System.Xml.Xsl.XslCompiledTransform>.

- L'analizzatore di espressioni XSLT viene caricato dal motore di debug gestito. Il motore di debug gestito presuppone che tutto il codice venga eseguito dal computer locale dell'utente. Di conseguenza, la classe <xref:System.Xml.Xsl.XslCompiledTransform> scarica il file XSLT nel computer locale dell'utente. La possibilità che possa verificarsi un'elevazione dei privilegi di esecuzione è attenuata dall'esecuzione di tutte le trasformazioni XSLT in un nuovo dominio applicazione con autorizzazioni limitate.

## <a name="see-also"></a>Vedi anche

- [Domini applicazione](/dotnet/framework/app-domains/application-domains)