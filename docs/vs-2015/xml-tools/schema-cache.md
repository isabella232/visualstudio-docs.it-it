---
title: Cache degli schemi | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 429dae6fdcd57da4d1d4db85df15966c20cc2aa5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528900"
---
# <a name="schema-cache"></a>Cache degli schemi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Cache degli schemi](https://docs.microsoft.com/visualstudio/xml-tools/schema-cache).  
  
  
L'editor XML fornisce una cache degli schemi situata nella directory %InstallRoot%\Xml\Schemas. La cache degli schemi è globale per tutti gli utenti di un computer e include gli schemi XML standard usati per la convalida dei documenti IntelliSense e XML.  
  
 L'editor XML può anche individuare gli schemi che si trova nella soluzione, gli schemi specificati nel **schemi** campo del documento **delle proprietà** finestra e gli schemi identificati dal `xsi:schemaLocation` e`xsi:noNamespaceSchemaLocation`degli attributi.  
  
 Nella tabella seguente vengono descritti gli schemi installati con l'editor XML.  
  
|Nomefile|Descrizione|  
|--------------|-----------------|  
|catalog.xsd|Schema per i file del catalogo schemi dell'editor XML. Per informazioni sui cataloghi degli schemi, vedere di seguito.|  
|DotNetConfig.xsd|Schema per i file Web. config, "http://schemas.microsoft.com/.NETConfiguration/v2.0".|  
|msbuild.xsd|Schema per i file, assicurarsi di MSBuild "http://schemas.microsoft.com/developer/msbuild/2003".|  
|msdata.xsd|Schema per le annotazioni XSD aggiunte dalla classe <xref:System.Data.DataSet>, "urn:schemas-microsoft-com:xml-msdata".|  
|msxsl.xsd|Schema per le estensioni del blocco di script Microsoft XSLT, urn:schemas-microsoft-com:xslt.|  
|SnippetFormat.xsd|Schema per i file XML del frammento di codice. Per esempi di schema, vedere %InstallDir%\VC#\Expansions.|  
|Soap1.1.xsd|Schema per Simple Object Access Protocol (SOAP) 1.1, http://schemas.xmlsoap.org/soap/envelope/.|  
|Soap1.2.xsd|Schema per il protocollo SOAP (Simple Object Access Protocol) 1.2.|  
|SiteMapSchema.xsd|Schema per il file XML di mappa del sito ASP.NET, "http://schemas.microsoft.com/AspNet/SiteMap-File-1.0".|  
|wsdl.xsd|Schema per Web Service Description Language, http://schemas.xmlsoap.org/wsdl/.|  
|xenc.xsd|Schema per la crittografia XML, http://www.w3.org/2000/09/xmldsig#.|  
|xhtml.xsd|Schema per XHTML http://www.w3.org/1999/xhtml.|  
|xlink.xsd|Schema per XLink 1.0, http://www.w3.org/1999/xlink.|  
|xml.xsd|Schema che descrive gli attributi XML: space e XML: lang, http://www.w3.org/XML/1998/namespace.|  
|xmlsig.xsd|Schema per le firme digitali XML http://www.w3.org/2000/09/xmldsig#.|  
|xsdschema.xsd|Schema che descrive XSD stesso, http://www.w3.org/2001/XMLSchema.|  
|xslt.xsd|Consente di trasformare lo schema per XML, http://www.w3.org/1999/XSL/Transform.|  
  
## <a name="updating-schemas-in-the-cache"></a>Aggiornamento degli schemi nella cache  
 L'editor carica la directory della cache di schema quando il package editor XML viene caricato e verifica le eventuali modifiche durante l'esecuzione. Se è stato aggiunto uno schema, esso viene caricato automaticamente in un indice di schemi noti in memoria. Se è stato rimosso uno schema, esso viene automaticamente rimosso dall'indice in memoria. Se è stato aggiornato uno schema, esso invalida automaticamente la cache degli schemi in memoria.  
  
> [!NOTE]
>  Poiché la directory della cache di schema è globale, è sufficiente aggiungere qui gli schemi standard utili per tutti i progetti di Visual Studio che è possibile creare sul proprio computer.  
  
 L'editor XML supporta inoltre un numero illimitato di file del catalogo degli schemi nella directory della cache. Per i cataloghi degli schemi è possibile scegliere altre posizioni per gli schemi che si desidera tenere sempre ben presenti nell'editor. Il file catalog.xsd definisce il formato del file di catalogo ed è incluso nella directory della cache degli schemi. Il file catalog.xml è il catalogo predefinito e contiene collegamenti ad altri schemi nella %InstallDir%. Di seguito sono riportati esempi del file catalog.xml:  
  
```  
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">  
  <Schema href="%InstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>  
  <Schema href="%InstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>  
  <Schema href="%InstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>  
</SchemaCatalog>  
```  
  
 L'attributo `href` può essere un qualsiasi percorso di file o URL di tipo http che fa riferimento allo schema. Il percorso del file può essere relativo al documento catalogo. Le seguenti variabili, delimitate da %%, sono riconosciute dall'editor e verranno espanse nel percorso:  
  
-   InstallDir  
  
-   Sistema  
  
-   ProgramFiles  
  
-   Programs  
  
-   CommonProgramFiles  
  
-   ApplicationData  
  
-   CommonApplicationData  
  
-   LCID  
  
 Nel documento catalogo può essere incluso un elemento `Catalog` che fa riferimento ad altri cataloghi. È possibile usare l'elemento `Catalog` per scegliere un catalogo centrale condiviso dal team o dalla società o un catalogo online condiviso con i partner commerciali. L'attributo `href` è il percorso del file o l'URL di tipo http per gli altri cataloghi. Di seguito è riportato un esempio dell'elemento `Catalog`:  
  
```  
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>  
```  
  
 Con il catalogo è inoltre possibile controllare in che modo gli schemi vengono associati ai documenti XML usando l'elemento speciale `Association`. Questo elemento consente di associare gli schemi che non dispongono di uno spazio dei nomi di destinazione con una determinata estensione di file. Questo può risultare utile in quanto l'editor XML non esegue l'associazione automatica degli schemi che non presentano un attributo `targetNamespace`. Nell'esempio seguente l'elemento `Association` associa lo schema dotNetConfig con tutti i file che presentano l'estensione "config":  
  
```  
<Association extension="config" schema="%InstallDir%/xml/schemas/dotNetConfig.xsd"/>  
```  
  
## <a name="localized-schemas"></a>Schemi localizzati  
 In molti casi il file catalog.xml non contiene voci per gli schemi localizzati. È possibile aggiungere ulteriori voci al file catalog.xml che fanno riferimento alla directory degli schemi localizzati.  
  
 Nell'esempio seguente è stato creato un nuovo elemento `Schema` che usa la variabile % LCID% per fare riferimento allo schema localizzato.  
  
```  
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"  
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>  
```  
  
## <a name="changing-the-location-of-the-schema-cache"></a>Modifica del percorso della cache degli schemi  
 È possibile personalizzare il percorso per la cache dello schema usando il **varie** pagina Opzioni. Se si dispone di una directory di schemi preferiti, è possibile configurare l'editor in modo da usare solo questi schemi.  
  
> [!NOTE]
>  Tale modifica ha effetto solo sull'utente corrente di Visual Studio.  
  
#### <a name="to-change-the-schema-cache-location"></a>Per modificare il percorso della cache degli schemi  
  
1.  Dal **degli strumenti** dal menu **opzioni**.  
  
2.  Espandere **Editor di testo**, espandere **XML**, quindi fare clic su **varie**.  
  
3.  Fare clic sul **esplorare** pulsante il **schemi** campo.  
  
4.  Selezionare la cartella della cache degli schemi e fare clic su **OK**.  
  
#### <a name="to-add-another-directory-of-common-schemas"></a>Per aggiungere un'altra directory di schemi comuni  
  
1.  Modificare il file catalog.xml nella directory della cache di schema dell'editor XML.  
  
2.  Aggiungere un nuovo elemento `<Catalog href="…"/>` che fa riferimento alla directory degli schemi aggiuntivi.  
  
3.  Salvare le modifiche.  
  
     Il catalogo viene ricaricato automaticamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)



