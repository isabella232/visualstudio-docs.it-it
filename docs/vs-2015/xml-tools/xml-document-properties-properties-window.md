---
title: Proprietà del documento XML, finestra Proprietà | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f620cc2bd189dccf067c6276f760d21cde5cf05e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669511"
---
# <a name="xml-document-properties-properties-window"></a>Proprietà dei documenti XML, finestra Proprietà
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella finestra **Proprietà** vengono fornite informazioni di base sul documento attivo nell'editor XML. Le proprietà disponibili variano in base al tipo di documento XML correntemente attivo.

> [!NOTE]
> Tutte le proprietà del documento XML vengono salvate nella soluzione. Di conseguenza, non sarà necessario immettere nuovamente tali valori alla successiva apertura della soluzione.

 **Codifica** Codifica dei caratteri per il file. Modificando questa proprietà si modifica anche l'attributo della codifica nella dichiarazione XML e viceversa. La nuova codifica verrà usata per codificare il file quando viene salvato.

 **Input** di Documento di input associato al foglio di stile XSLT. Viene usato dal comando **output ShowXSLT** . È possibile selezionare un documento utilizzando il pulsante Sfoglia (**..**.).

 Questa proprietà è visibile solo quando il file XSLT è correntemente attivo nella finestra dell'editor.

 **Output** di File generato durante la trasformazione di un documento XML.

 Se un file non è specificato, verrà generato un nome file predefinito in base all'attributo `method` dell'elemento `xsl:output` che determina l'estensione del file. Il file predefinito si trova nella directory temporanea dell'utente corrente.

 **Schemi** di Schemi da utilizzare per la convalida. Il pulsante consente di aprire la finestra di dialogo **schemi XSD** , che può essere utilizzata per selezionare gli schemi da utilizzare.

 È possibile anche immettere il percorso degli schemi. Se vengono specificati più schemi, ogni singolo percorso di schema deve essere racchiuso tra virgolette.

 **Foglio di stile** File XSLT utilizzato per trasformare il documento quando viene utilizzato il comando **Mostra output XSLT** . Se questo campo è vuoto quando si utilizza il comando **Mostra output XSLT** , l'editor utilizzerà il valore specificato nell' `xml-stylesheet` istruzione di elaborazione del documento oppure verrà richiesto di specificare il nome del file.

 Quando si modifica un file XSLT, questa proprietà può essere utilizzata per specificare che deve essere utilizzato un foglio di stile diverso quando si seleziona il comando **Mostra output XSLT** o **debug XSLT** . Ad esempio, è possibile eseguire tale operazione quando si modifica un foglio di stile incluso in un foglio di stile padre.

## <a name="see-also"></a>Vedere anche
 [Componenti dell'editor](../xml-tools/xml-editor-components.md) XML dell' [editor XML](../xml-tools/xml-editor.md)
