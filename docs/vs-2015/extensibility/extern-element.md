---
title: Elemento extern | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17477b7eb60aa332f6910019e28f4c53aa31ebf1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204405"
---
# <a name="extern-element"></a>Elemento Extern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'elemento extern fa riferimento a qualsiasi file di intestazione esterna (. h) da unire con il file vsct in fase di compilazione. I file da unire devono trovarsi nel percorso di inclusione assegnato al compilatore VSCT o a cui fa riferimento un [elemento include](../extensibility/include-element.md). I file possono essere altri file con estensione vsct o file di intestazione C++.  
  
 Le definizioni nei file di intestazione devono essere nel formato "#define [Symbol] [valore]". il valore può essere un altro simbolo se è stato definito in precedenza. Le definizioni possono essere utilizzate nelle istruzioni condizionali degli elementi di comando. Qualsiasi simbolo non effettivamente usato verrà rimosso.  
  
 Elemento CommandTable  
Elemento Extern  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|href|Obbligatorio. Percorso del file di intestazione:<br /><br /> href = "Stdidcmd. h"|  
|Condizione|facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|Linguaggio|facoltativo. Lingua predefinita di tutti [\<Strings>](../extensibility/strings-element.md) gli elementi nella tabella dei comandi:<br /><br /> lingua = "en-US"|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Nessuno.|Nessuno.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi, ovvero le voci di menu, i menu, le barre degli strumenti e le caselle combinate, fornite da un pacchetto VSPackage all'IDE.|  
  
## <a name="example"></a>Esempio  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    …  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tabella comandi di Visual Studio (. File vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
