# fdfgfd

 {
    method: "GET",
    path: "/aboutus",
    handler: async (req, h) => {
      let mst = 10
      let privArray = [
        {
          privNumber: 1,
          status: 999
        },
        {
          privNumber: 2,
          status: 999
        },
        {
          privNumber: 4,
          status: 999
        }
      ]
      let promArray = []
      for (const eac of privArray) {
        promArray.push(
          JSON.stringify(
            new Promise(async (resolve)=>{
              await knex.raw(`UPDATE roles SET rp_status =  ${eac.status}  WHERE mst = ${mst} and rp = ${eac.privNumber}`).then(([eee]) => {
                // console.log(eee)
                // data = eee
                resolve(eee)
              })
            })
          )
          
        )
        
       
        // console.log(`UPDATE roles SET rp_status = ${eac.status} WHERE mst = ${mst} and rp = ${eac.privNumber}`)
      }

      // await Promise.all(promArray).then((f)=>{
      //   console.log(f)
      // })
      // let data = []
      // await knex.raw(`SELECT * FROM roles`).then(([eee]) => {
      //   console.log(eee)
      //   data = eee
      // })
      


    
      return {
        success: true,
        message: "",
        // data
      };
    }
  },
