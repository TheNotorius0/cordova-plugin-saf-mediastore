# cordova-plugin-saf-mediastore

## Notorious' changes

Removed the permissions "READ_EXTERNAL_STORAGE" and "WRITE_EXTERNAL_STORAGE" in order to be compliant with Google Play Games on PC (Beta)

## Read and save files using the Storage Access Framework and Mediastore

This plugin allows you to read and save files using the Storage Access Framework and Mediastore on Android only.

## Available methods

```typescript
selectFolder(uri:string):Promise<string>
```

Launches an Intent to select a folder to which files can be saved. Returns the content URI.

```typescript
selectFile(uri:string):Promise<string>
```

Launches an Intent to select a file. Returns the content URI.

```typescript
openFolder(uri:string):Promise<void>
```

Launches an Intent to open a folder in the folder picker.

```typescript
openFile(uri:string):Promise<void>
```

Launches an Intent to open a file.

```typescript
readFile(uri:string):Promise<ArrayBuffer>
```

Reads a file as an ArrayBuffer.

```typescript
writeFile(params:{
	data:string,
	filename:string,
	folder?:string,
	subFolder?:string
}):Promise<string>
```

Writes a file to a specific filename, with the folder and subfolder being optional. The subfolder will be created if it does not exist, and the default folder is the Downloads folder (saved via Mediastore). Returns the content URI. `data` is a Base 64 string.

```typescript
overwriteFile(params:{
    uri:string,
    data:string
}):Promise<string>
```

Overwrites a file at a specific content URI. Returns the content URI.

```typescript
saveFile(params:{
	data:string,
	filename?:string,
	folder?:string
}):Promise<string>
```

Launches a file picker Intent to save a file, with the preferred filename and folder being optional. Returns the content URI. `data` is a Base 64 string.

```typescript
deleteFile(uri:string):Promise<number>
```

Deletes a file at a specific content URI. Returns the number of files deleted.

```typescript
getFileName(uri:string):Promise<string>
```

Returns the filename of the corresponding content URI.

```typescript
getUri(params:{
    folder:string,
    subFolder?:string,
    filename?:string,
}):Promise<string>
```

Returns the content URI of the file in the corresponding folder and subfolder.

```typescript
existsFile(filename: string): Promise<string>;
```

From a filename check if the files exist in the shared download folder return uri of the corresponding file if exists, otherwise return -1

```typescript
getDataForOpenFile(uri: string): Promise<{
    uri: string;
    mimeType: string;
    filename: string;
  }>;
```

From Content URI return information about the file

To call methods:

```typescript
cordova.plugins.safMediastore.<function>(params); //returns a Promise
await cordova.plugins.safMediastore.<function>(params); //in an async function
```
