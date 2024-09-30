import fs from "fs";
import OpenAI from "openai";

const openai = new OpenAI();

async function main() {
    try {
        const image = await openai.images.createVariation({
            image: fs.createReadStream("image.png"),
            n: 1,
            size: "1024x1024",
        });
        console.log(image.data);
    } catch (error) {
        if (error.response) {
            console.log(error.response.status);
            console.log(error.response.data);
        } else {
            console.log(error.message);
        }
    }
}

main();
