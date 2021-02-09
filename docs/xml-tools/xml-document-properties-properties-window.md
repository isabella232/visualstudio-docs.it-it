---
title: Proprietà dei documenti XML, finestra Proprietà
description: Informazioni sulle proprietà dei documenti XML nel Finestra Proprietà che forniscono informazioni di base sul documento attivo nell'editor XML.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e12118f2f7f5d9189ca768f7be65a35b490eb54
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875016"
---
# <a name="xml-document-properties-properties-window"></a>Proprietà del documento XML, Finestra Proprietà

Nella finestra **Proprietà** vengono fornite informazioni di base sul documento attivo nell'editor XML. Le proprietà disponibili variano in base al tipo di documento XML correntemente attivo.

> [!NOTE]
> Tutte le proprietà del documento XML vengono salvate nella soluzione. Di conseguenza, non sarà necessario immettere nuovamente tali valori alla successiva apertura della soluzione.

**Encoding**

La codifica dei caratteri per il file. Modificando questa proprietà si modifica anche l'attributo della codifica nella dichiarazione XML e viceversa. La nuova codifica viene utilizzata per codificare il file quando si salva il file.

**Input**

Il documento di input associato al foglio di stile XSLT. Viene usato dai comandi di **avvio XSLT** , ad esempio, **XML**  >  **Start XSLT senza debug**. È possibile selezionare un documento utilizzando il pulsante Sfoglia (**..**.).

Questa proprietà è visibile solo quando un file XSLT è aperto nell'editor.

**Output**

Il file che viene generato durante la trasformazione di un documento XML.

Se non viene specificato alcun file, viene generato un nome file predefinito in base all' `method` attributo dell' `xsl:output` elemento, che determina l'estensione del file. Il file predefinito si trova nella directory temporanea dell'utente corrente.

**Schemi**

Gli schemi da usare per la convalida. Il pulsante consente di aprire la finestra di dialogo **schemi XSD** , che può essere utilizzata per selezionare gli schemi da utilizzare.

È possibile anche immettere il percorso degli schemi. Se vengono specificati più schemi, ogni singolo percorso di schema deve essere racchiuso tra virgolette.

**StyleSheet**

Il file XSLT utilizzato per trasformare il documento quando vengono utilizzati i comandi **Avvia XSLT debug** e **Avvia XSLT senza debug** . Se questo campo è vuoto, l'editor utilizzerà il valore specificato nell' `xml-stylesheet` istruzione di elaborazione del documento oppure verrà richiesto di specificare un nome file.

Quando si modifica un file XSLT, questa proprietà può essere usata per specificare che è necessario usare un foglio di stile diverso quando si seleziona il comando **Avvia il debug XSLT** o **Avvia XSLT senza debug** . Questa operazione può essere eseguita, ad esempio, quando si modifica un foglio di stile incluso in un foglio di stile padre.

## <a name="see-also"></a>Vedi anche

- [Editor XML](../xml-tools/xml-editor.md)
