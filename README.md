# Demo

Some description!

## Subheader

    Learning tutorial

Testing changes
Change
GIT URL
Testing Folder Creation
Testing Zip
Won't work!!!
I am here..
We have hope
testing!!

function getDirectoryContents(highDir, folderPath, folderName)
      {
        app.log.info("Made it inside function")
        const newFolder = highDir.folder(folderName)
        fs.readdir(folderPath, function(err, files){
          if(err){
            app.log.info(err);
          }

          files.forEach((file) => {
            //app.log.info(file);
            const newPath = folderPath + "\\" + file;
            app.log.info(newPath);

            var nStats = fs.statSync(newPath);
            if(nStats.isFile())
            {
              const data = fs.readFileSync(newPath);
              newFolder.file(file, data);
            } else if(nStats.isDirectory())
            {
              var descendant = getDirectoryContents(newFolder, newPath, file)
            }
          })
          
        })
        return newFolder;
      }

      async function createZip()
      {
        files.forEach((file) => {
          //app.log.info(file);
          const filePath = directoryPath+"\\"+file;
          app.log.info(filePath);
          
          var stats = fs.statSync(filePath);
          //app.log.info(stats.isFile());
          if(stats.isFile())
          {
            const fileData = fs.readFileSync(filePath);
            zip.file(file, fileData);
          } else if (stats.isDirectory()) {
            var curFolder = await getDirectoryContents(zip, filePath, file);
          }
          
          
        });
      }