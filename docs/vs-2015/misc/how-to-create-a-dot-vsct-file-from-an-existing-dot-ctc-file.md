---
title: 'Procedura: creare una. File Vsct da un oggetto esistente. File CTC | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, creating based on a .ctc file
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: 0d267e6046539001cbe454ab69867c02f0a606ed
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530259"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Procedura: Creare un file con estensione vsct da un file CTC esistente
È possibile creare un file con estensione vsct basato su XML da un file di origine CTC esistente della tabella comandi. In questo modo, è possibile sfruttare i vantaggi del nuovo basato su XML [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] comando nel formato del compilatore tabella (VSCT).  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Per creare un file con estensione vsct da un file CTC  
  
1.  Ottenere una copia del linguaggio Perl.  
  
2.  Ottenere una copia dello script Perl ConvertCTCToVSCT.pl, in genere si trova nel  *\<percorso di installazione di Visual Studio SDK >* \visualstudiointegration\tools\bin. cartella.  
  
3.  Ottenere una copia del file di origine CTC da convertire.  
  
4.  Inserire i file nella stessa directory.  
  
5.  Nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] finestra Prompt dei comandi, passare alla directory.  
  
6.  Digitare  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     dove PkgCmd.ctc è il nome del file CTC e PkgCmd.vsct è il nome del file con estensione vsct da creare.  
  
     Verrà creato un nuovo file di origine XML della tabella comandi con estensione vsct. È possibile compilare il file con Vsct.exe, il compilatore VSCT, come si farebbe con qualsiasi altro file con estensione vsct.  
  
    > [!NOTE]
    >  È possibile migliorare la leggibilità del file con estensione vsct riformattando i commenti XML.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare una. File Vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)