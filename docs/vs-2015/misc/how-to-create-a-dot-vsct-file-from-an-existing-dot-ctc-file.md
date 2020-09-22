---
title: 'Procedura: creare un oggetto. File vsct da un esistente. File CTC | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .ctc file
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 7b963436e9d968dd5ba3829e97d0fd0c52e49641
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839540"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Procedura: Creare un file con estensione vsct da un file CTC esistente
È possibile creare un file con estensione vsct basato su XML da un file di origine CTC esistente della tabella comandi. In questo modo, si può sfruttare il nuovo formato basato su XML del compilatore della tabella comandi di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (VSCT).  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Per creare un file con estensione vsct da un file CTC  
  
1. Ottenere una copia del linguaggio Perl.  
  
2. Ottenere una copia dello script Perl ConvertCTCToVSCT.pl, che si trova in genere nella *\<Visual Studio SDK installation path>* cartella \VisualStudioIntegration\Tools\bin  
  
3. Ottenere una copia del file di origine CTC da convertire.  
  
4. Inserire i file nella stessa directory.  
  
5. Nella finestra del prompt dei comandi di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spostarsi nella directory.  
  
6. Type  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     dove PkgCmd.ctc è il nome del file CTC e PkgCmd.vsct è il nome del file con estensione vsct da creare.  
  
     Verrà creato un nuovo file di origine XML della tabella comandi con estensione vsct. È possibile compilare il file con Vsct.exe, il compilatore VSCT, come si farebbe con qualsiasi altro file con estensione vsct.  
  
    > [!NOTE]
    > È possibile migliorare la leggibilità del file con estensione vsct riformattando i commenti XML.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un oggetto. File vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)