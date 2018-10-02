---
title: Proprietà del documento XML, finestra proprietà | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7145c81a87235d37a0e4825509e7f8fb94ab0f7c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540421"
---
# <a name="xml-document-properties-properties-window"></a>Proprietà dei documenti XML, finestra Proprietà
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [proprietà del documento XML, finestra proprietà](https://docs.microsoft.com/visualstudio/xml-tools/xml-document-properties-properties-window).  
  
  
Il **proprietà** finestra fornisce informazioni di base relative al documento attivo nell'Editor XML. Le proprietà disponibili variano in base al tipo di documento XML correntemente attivo.  
  
> [!NOTE]
>  Tutte le proprietà del documento XML vengono salvate nella soluzione. Di conseguenza, non sarà necessario immettere nuovamente tali valori alla successiva apertura della soluzione.  
  
 **Codifica**  
 La codifica dei caratteri per il file. Modificando questa proprietà si modifica anche l'attributo della codifica nella dichiarazione XML e viceversa. La nuova codifica verrà usata per codificare il file quando viene salvato.  
  
 **Input**  
 Il documento di input associato al foglio di stile XSLT. Viene usato per il **ShowXSLT Output** comando. Un documento può essere selezionato utilizzando il pulsante Sfoglia (**...** ) pulsante.  
  
 Questa proprietà è visibile solo quando il file XSLT è correntemente attivo nella finestra dell'editor.  
  
 **Output**  
 Il file che viene generato durante la trasformazione di un documento XML.  
  
 Se un file non è specificato, verrà generato un nome file predefinito in base all'attributo `method` dell'elemento `xsl:output` che determina l'estensione del file. Il file predefinito si trova nella directory temporanea dell'utente corrente.  
  
 **Schemi**  
 Gli schemi da usare per la convalida. Il pulsante apre il **schemi XSD** nella finestra di dialogo può essere usata per selezionare gli schemi da usare.  
  
 È possibile anche immettere il percorso degli schemi. Se vengono specificati più schemi, ogni singolo percorso di schema deve essere racchiuso tra virgolette.  
  
 **Foglio di stile**  
 Il file XSLT utilizzato per trasformare il documento quando la **Mostra l'Output XSLT** comando viene utilizzato. Se questo campo è vuoto quando il **Mostra l'Output XSLT** comando viene utilizzato, l'editor utilizzerà il valore fornito nel `xml-stylesheet` istruzione del documento o di elaborazione richiede il nome del file.  
  
 Quando si modifica un file XSLT, questa proprietà può essere utilizzata per specificare che deve essere un foglio di stile utilizzato quando la **Mostra l'Output XSLT** o **Debug XSLT** comando selezionato. Ad esempio, è possibile eseguire tale operazione quando si modifica un foglio di stile incluso in un foglio di stile padre.  
  
## <a name="see-also"></a>Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)   
 [Componenti dell'editor XML](../xml-tools/xml-editor-components.md)



