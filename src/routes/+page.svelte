<script>
  let userInput = '';
  let messages = [];

  const responseMap = {
    'start': "At the start of your quest, help arrives from metal beasts. Seek where they rest when tasks are done, vehicles groomed one by one. This is the first clue so I'll let you off easy, head to 57 John Street, Northbridge",
    'let': "Blades fly true when aimed with skill, At wooden targets, thrill after thrill. This modern sport's primal cry, Points where axes rent the sky. One more hint, it's really close by.",
    'the': "Where ancient relics find their home, Preserved for all to explore and roam. Exhibits rich with history's trace, Guide you to this hallowed place.",
    '5683': "Welcome to Tall Tree Adventures Natasha and Jacinta! You're booked in a for a whole days adventure around Perth city, so first let me give you your instructions. Throughout the day you will receive cards such as the one you are holding. Each will have a keyword on it. Type in the keyword and it will provide the next clue. If you retype the keyword, the clue will repeat itself. Type 'clear' to clear the messages on the screen and to make space. To get started, clear the chat if your wish, then type your first keyword 'Start'. Remember to bring the clue cards around with you for the day.",
    'show': "Worlds of stories, fact and fiction, Bound between covers, a literary addiction. This planet's orbital pull is strong,   Attracting readers where tales belong.",
    'world.': "Russell Square's greenery hides, A lock that your key's use abides. From humble origins did it start, That metal prize must play its part. When boughs with purple blossoms bloom, A vivid scene for all to consume.",
    'me': "Secrets unlocked by your key's turn, Yield one more, its use you'll soon learn. To a sanctuary of love you must go, Where crimson robes await their ruby glow. A cherished place, your next warm phase, That familiar domestic base.",
    'please': "Where shooting sports and oak-aged vintages meet, Retrace your love's first tender heartbeats. A tavern feast where romance took aim, Let cherished archives reignite that flame. Relive the scene that started your trail, Over pints and plates, a timeless tale.",
    'you': " Put together your keywords, minus the 'start', and you will hear these words from my hearts. Our game is done, this is the final clue, this sentence reveals, my message to you. The next phase awaits, the future to write, Let love's radiant question take flight. This foreshore bred infinite joys in its wake, Now let new vows be joyfully stake. The trail concludes where it first did start, United, you'll embark with two thunded as one heart.",
    'clear': 'A fresh start',
  };

  function handleUserInput() {
    const trimmedInput = userInput.trim().toLowerCase();
    let response = '';

    for (const keyword in responseMap) {
      if (trimmedInput.includes(keyword)) {
        response = responseMap[keyword];
        console.log(response)
        break;
      } else {
        response = "That doesn't seem to be a valid keyword for your adventure, try again"
      }
    } 

    if (response == 'A fresh start') {
      messages = [{ sender: 'user', text: userInput }, { sender: 'bot', text: response }];
      userInput = '';
    } else {
      messages = [...messages, { sender: 'user', text: userInput }, { sender: 'bot', text: response }];
      userInput = '';
    }
  }
</script>

<div class=" min-h-screen flex flex-col items-center bg-yellow-200">
  <h1 class="text-5xl md:text-6xl barlow-semi-condensed-extrabold-italic text-blue-950 my-4 text-center">Tall Tree Adventures</h1>
  <div class="f mt-8 flex flex-col w-5/6 md:w-1/4">
    {#each messages as message}
      <div class={message.sender== 'bot' ? 'text-gray-50 bg-green-500 rounded-lg p-3 w-3/5 mb-4 self-end' : ' text-gray-50 bg-blue-500 rounded-lg p-3 w-3/5 mb-4 self-start mr-auto'}>
        {message.text}
      </div>
    {/each}
  </div>
  <div class=" w-5/6 md:w-1/4 ">
    <input class="block w-full bg-yellow-100 rounded-md border-0 py-1.5 px-2 text-gray-700 shadow-sm ring-1 ring-inset ring-yellow-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-yellow-600 sm:text-sm sm:leading-6" type="text" bind:value={userInput} on:keydown={(e) => e.key === 'Enter' && handleUserInput()} placeholder="Type your message here..." />
  </div>
</div>

<style>
  /* Add your styles here */

.barlow-semi-condensed-extrabold-italic {
  font-family: "Barlow Semi Condensed", sans-serif;
  font-weight: 800;
  font-style: italic;
}

</style>


