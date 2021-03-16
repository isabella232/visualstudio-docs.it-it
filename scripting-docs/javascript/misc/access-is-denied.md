---
description: Uno script ha cercato di accedere ai dati da un'origine diversa dall'host della pagina corrente.
title: Accesso negato | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 6be3bce0643a5892973235871191766cac140962
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571935"
---
# <a name="access-is-denied"></a>Accesso negato
Uno script ha cercato di accedere ai dati da un'origine diversa dall'host della pagina corrente. I criteri di corrispondenza dell'origine seguiti da Internet Explorer e da altri browser consentono agli script di accedere ai dati solo da origini con lo stesso schema, host e porta dell'URL della pagina corrente.  
  
 Ad esempio, se la pagina corrente è `https://employees.mycompany.com` , non è possibile accedere ai dati dagli URL seguenti:  
  
- `http://data.contoso.com`, perché usa HTTP anziché HTTPS.  
  
- `https://somedatasource.com`, perché si tratta di un dominio diverso.  
  
- `https://employees.mycompany.com:8888`, perché usa una porta diversa.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Controllare se l'API che si sta cercando di chiamare supporta JSONP o CORS, due approcci che consentono lo scripting tra le origini in modo sicuro.  
  
- Se si sta cercando di chiamare un'API REST, effettuare il refactoring di questa chiamata al codice lato server, quindi esporre un nuovo endpoint REST per gli script lato client.  
  
     Per altre informazioni, cercare la documentazione online relativa ai criteri di corrispondenza dell'origine, a JSONP e a CORS.
