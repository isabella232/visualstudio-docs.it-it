---
title: Accesso negato | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9b49f60395a853d7dfda91738ccccaba9d585b46
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295163"
---
# <a name="access-is-denied"></a>Accesso negato
Uno script ha cercato di accedere ai dati da un'origine diversa dall'host della pagina corrente. I criteri di corrispondenza dell'origine seguiti da Internet Explorer e da altri browser consentono agli script di accedere ai dati solo da origini con lo stesso schema, host e porta dell'URL della pagina corrente.  
  
 Ad esempio, se la pagina corrente è `https://employees.mycompany.com`, è possibile accedere ai dati dagli URL seguenti:  
  
-   `http://data.contoso.com`, perché Usa HTTP anziché HTTPS.  
  
-   `https://somedatasource.com`, perché è un dominio diverso.  
  
-   `https://employees.mycompany.com:8888`, perché usa una porta diversa.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Controllare se l'API che si sta cercando di chiamare supporta JSONP o CORS, due approcci che consentono lo scripting tra le origini in modo sicuro.  
  
-   Se si sta cercando di chiamare un'API REST, effettuare il refactoring di questa chiamata al codice lato server, quindi esporre un nuovo endpoint REST per gli script lato client.  
  
     Per altre informazioni, cercare la documentazione online relativa ai criteri di corrispondenza dell'origine, a JSONP e a CORS.
