---
description: Descrive un'istruzione Disassembly per la visualizzazione del Integrated Development Environment (IDE).
title: DisassemblyData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b6053647d43563e7369793982c72683002ae0df5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170458"
---
# <a name="disassemblydata"></a>DisassemblyData
Descrive un'istruzione Disassembly per la visualizzazione del Integrated Development Environment (IDE).

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagDisassemblyData {
    DISASSEMBLY_STREAM_FIELDS dwFields;
    BSTR                      bstrAddress;
    BSTR                      bstrAddressOffset;
    BSTR                      bstrCodeBytes;
    BSTR                      bstrOpcode;
    BSTR                      bstrOperands;
    BSTR                      bstrSymbol;
    UINT64                    uCodeLocationId;
    TEXT_POSITION             posBeg;
    TEXT_POSITION             posEnd;
    BSTR                      bstrDocumentUrl;
    DWORD                     dwByteOffset;
    DISASSEMBLY_FLAGS         dwFlags;
} DisassemblyData;
```

```csharp
public struct DisassemblyData { 
    public uint          dwFields;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrCodeBytes;
    public string        bstrOpcode;
    public string        bstrOperands;
    public string        bstrSymbol;
    public ulong         uCodeLocationId;
    public TEXT_POSITION posBeg;
    public TEXT_POSITION posEnd;
    public string        bstrDocumentUrl;
    public uint          dwByteOffset;
    public uint          dwFlags;
};
```

## <a name="members"></a>Members
`dwFields`\
Costante [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) che specifica i campi che vengono compilati.

`bstrAddress`\
Indirizzo come offset da un punto iniziale, in genere l'inizio della funzione associata.

`bstrCodeBytes`\
Byte di codice per questa istruzione.

`bstrOpcode`\
Codice operativo per questa istruzione.

`bstrOperands`\
Operandi per questa istruzione.

`bstrSymbol`\
Il nome del simbolo, se presente, associato all'indirizzo (simbolo pubblico, etichetta e così via).

`uCodeLocationId`\
Identificatore del percorso del codice per questa linea disassemblata. Se l'indirizzo del contesto del codice di una riga è maggiore dell'indirizzo del contesto del codice di un altro, l'identificatore del percorso del codice disassemblato del primo sarà anche maggiore dell'identificatore del percorso del codice del secondo.

`posBeg`\
Il [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) che corrisponde alla posizione in un documento in cui iniziano i dati di Disassembly.

`posEnd`\
[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) che corrisponde alla posizione in un documento in cui terminano i dati del Disassembly.

`bstrDocumentUrl`\
Per i documenti di testo che possono essere rappresentati come nomi di file, il `bstrDocumentUrl` campo viene compilato con il nome del file in cui è possibile trovare l'origine, usando il formato `file://file name` .

Per i documenti di testo che non possono essere rappresentati come nomi di file, `bstrDocumentUrl` è un identificatore univoco per il documento e il motore di debug deve implementare il metodo [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) .

Questo campo può inoltre contenere informazioni aggiuntive sui checksum. Per ulteriori informazioni, vedere Note.

`dwByteOffset`\
Il numero di byte che l'istruzione è dall'inizio della riga di codice.

`dwFlags`\
Costante [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) che specifica i flag attivi.

## <a name="remarks"></a>Commenti
Ogni `DisassemblyData` struttura descrive un'istruzione del Disassembly. Una matrice di queste strutture viene restituita dal metodo [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .

La struttura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) viene utilizzata solo per i documenti basati su testo. L'intervallo di codice sorgente per questa istruzione viene compilato solo per la prima istruzione generata da un'istruzione o una riga, ad esempio quando `dwByteOffset == 0` .

Per i documenti non testuali, è possibile ottenere un contesto del documento dal codice e il `bstrDocumentUrl` campo deve essere un valore null. Se il `bstrDocumentUrl` campo è uguale al `bstrDocumentUrl` campo nell'elemento di matrice precedente `DisassemblyData` , impostare `bstrDocumentUrl` su un valore null.

Se `dwFlags` per il campo è `DF_DOCUMENT_CHECKSUM` impostato il flag, le informazioni aggiuntive sul checksum seguono la stringa a cui punta il `bstrDocumentUrl` campo. In particolare, dopo il carattere di terminazione della stringa null, segue un GUID che identifica l'algoritmo di checksum a sua volta seguito da un valore a 4 byte che indica il numero di byte nel checksum e che a sua volta è seguito dai byte di checksum. Vedere l'esempio in questo argomento su come codificare e decodificare questo campo in [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

## <a name="example"></a>Esempio
`bstrDocumentUrl`Se il `DF_DOCUMENT_CHECKSUM` flag è impostato, il campo può contenere informazioni aggiuntive diverse da una stringa. Il processo di creazione e lettura di questa stringa codificata è semplice in [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] . In, tuttavia, [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] è un altro aspetto. Per chi è curioso, nell'esempio seguente viene illustrato un modo per creare la stringa codificata da [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] e un modo per decodificare la stringa codificata in [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
    class MyClass
    {
        string EncodeData(string documentString,
                          Guid checksumGuid,
                          byte[] checksumData)
        {
            string returnString = documentString;

            if (checksumGuid == null || checksumData == null)
            {
                // Nothing more to do. Just return the string.
                return returnString;
            }

            returnString += '\0'; // separating null value

            // Add checksum GUID to string.
            byte[] guidDataArray  = checksumGuid.ToByteArray();
            int    guidDataLength = guidDataArray.Length;
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);
            for (int i = 0; i < guidDataLength; i++)
            {
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);
            }
            // Copy guid data bytes to string as wide characters.
            // Assumption: sizeof(char) == 2.
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum count (a 32-bit value).
            Int32 checksumCount = checksumData.Length;
            Marshal.StructureToPtr(checksumCount, pBuffer, true);
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum data.
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);
            for (int i = 0; i < checksumCount; i++)
            {
                Marshal.WriteByte(pBuffer, i, checksumData[i]);
            }
            for (int i = 0; i < checksumCount / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }
            Marshal.FreeCoTaskMem(pBuffer);

            return returnString;
        }

        void DecodeData(    string encodedString,
                        out string documentString,
                        out Guid   checksumGuid,
                        out byte[] checksumData)
        {
            documentString = String.Empty;
            checksumGuid = Guid.Empty;
            checksumData = null;

            IntPtr pBuffer = Marshal.StringToBSTR(encodedString);
            if (null != pBuffer)
            {
                int bufferOffset = 0;

                // Parse string out. String is assumed to be Unicode.
                documentString = Marshal.PtrToStringUni(pBuffer);
                bufferOffset += (documentString.Length + 1) * sizeof(char);

                // Parse Guid out.
                // Read guid bytes from buffer and store in temporary
                // buffer that contains only the guid bytes. Then the
                // Marshal.PtrToStructure() can work properly.
                byte[] guidDataArray  = checksumGuid.ToByteArray();
                int    guidDataLength = guidDataArray.Length;
                IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);
                for (int i = 0; i < guidDataLength; i++)
                {
                    Marshal.WriteByte(pGuidBuffer, i,
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
                }
                bufferOffset += guidDataLength;
                checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));
                Marshal.FreeCoTaskMem(pGuidBuffer);

                // Parse out the number of checksum data bytes (always 32-bit value).
                int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);
                bufferOffset += sizeof(Int32);

                // Parse out the checksum data.
                checksumData = new byte[dataCount];
                for (int i = 0; i < dataCount; i++)
                {
                    checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
