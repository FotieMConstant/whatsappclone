<template>
  <span>
    <v-row no-gutters>
      <v-col cols="12" md="4">
        <v-card outlined tile>
          <!-- top left bar -->
          <TopLeftBar />
          <Search @onFilterFromChild="filterChatList" />
          <div class="__sideChatList">
            <span v-for="chat in chatsList" :key="chat.id" class="__chatItem">
              <ChatItem :chat="chat" @onClickToViewInboxFromChild="returnChatObject" />
            </span>
          </div>
        </v-card>
      </v-col>
      <v-col cols="12" md="8">
        <Inbox :chat="chatObjectToViewInInbox" :chatsList="chatsList" />
      </v-col>
    </v-row>
  </span>
</template>

<script>
import TopLeftBar from "../components/TopLeftBar";
import ChatItem from "../components/ChatItem";
import Search from "../components/Search";
import Inbox from "../components/Inbox";

export default {
  name: "Home",

  components: {
    TopLeftBar,
    ChatItem,
    Search,
    Inbox,
  },
  data() {
    return {
      chatObjectToViewInInbox: {}, // variable to keep the preview chat in inbox
      chatsList: [
        {
          id: 0,
          name: "Kelly",
          lastMessage: "Hey man, what's up?",
          lastTextTime: "Yesterday",
          totalMessagesInChat: 7,
          blueCheck: true,
          lastSeen: "online",
          displayPicture:
            "https://s11.favim.com/orig/7/766/7668/76682/black-girls-profile-kinky-hair-Favim.com-7668211.jpg",
          messages: [
            {
              received: "Hey man",
              sent: "Hey, sup?",
              timeStampSent: "15:05",
              timeStampReceived: "11:24",
            },
            {
              received: "Yumm! Yammy, i guess you enjoyed, lol",
              sent: "Not really, was not enough for me.. lol😂😂",
              timeStampSent: "01:05",
              timeStampReceived: "15:24",
            },
            {
              received: "😂 ... as much as i thought",
              sent: "... you know me!",
              timeStampSent: "10:05",
              timeStampReceived: "19:24",
            },
          ],
        },
        {
          id: 1,
          name: "好朋友",
          lastMessage: "同学们好！谁用微信？",
          lastTextTime: "15:30",
          totalMessagesInChat: 1,
          blueCheck: true,
          lastSeen: "14:50",
          displayPicture:
            "https://blog.keatschinese.com/wp-content/uploads/2020/12/learning-the-chinese-language.jpg",
          messages: [
            {
              received: "你好",
              sent: "你好,怎么样?",
              timeStampSent: "18:05",
              timeStampReceived: "10:24",
            },
            {
              received: "好久不见",
              sent: "对呀, 好久不见! 你最近在忙什么？",
              timeStampSent: "17:50",
              timeStampReceived: "07:05",
            },
            {
              received: "没什么，你呢？",
              sent: "一样的，没什么特别的!",
              timeStampSent: "15:05",
              timeStampReceived: "13:24",
            },
            {
              received: "好的, 你什么时候回中国?",
              sent: "我还不确定什么时候, 但我一定会让你知道!",
              timeStampSent: "23:05",
              timeStampReceived: "15:24",
            },
          ],
        },
        {
          id: 2,
          name: "yancodes",
          lastMessage: "The same guy I was with the last time I was there",
          lastTextTime: "07:15",
          totalMessagesInChat: 12,
          blueCheck: false,
          lastSeen: "18:40",
          displayPicture:
            "https://pbs.twimg.com/profile_images/1172588555966844933/GD3slkzF_400x400.jpg",
          messages: [
            {
              received: "Yo bro",
              sent: "Yo",
              timeStampSent: "10:05",
              timeStampReceived: "11:24",
            },
            {
              received: "What's up?",
              sent: "nothing much",
              timeStampSent: "18:05",
              timeStampReceived: "11:24",
            },
            {
              received:
                "I heard you are building a whatapp clone, lol! Courage! Hehehe",
              sent: "Yeah i am, and almost done, just working on the ui tho, no backend",
              timeStampSent: "15:05",
              timeStampReceived: "11:24",
            },
            {
              received: "Oh, i see",
              sent: "yeah",
              timeStampSent: "18:05",
              timeStampReceived: "18:24",
            },
          ],
        },
        {
          id: 3,
          name: "Longla",
          lastMessage: "Thanks bro",
          lastTextTime: "Yesterday",
          totalMessagesInChat: 1,
          blueCheck: false,
          lastSeen: "1:10",
          displayPicture:
            "https://avatars.githubusercontent.com/u/44490676?v=4",
          messages: [
            {
              received: "Yo Wowo man",
              sent: "Yo man",
              timeStampSent: "15:05",
              timeStampReceived: "11:24",
            },
            {
              received: "You fit get 5k for your momo?",
              sent: "No man, sorry!",
              timeStampSent: "15:05",
              timeStampReceived: "11:24",
            },
            {
              received: "No worries man, ah go hustle different man",
              sent: "okay pa!",
              timeStampSent: "15:05",
              timeStampReceived: "11:24",
            },
            {
              received: "Thanks though",
              sent: "No problem",
              timeStampSent: "15:05",
              timeStampReceived: "11:24",
            },
          ],
        },
        {
          id: 4,
          name: "Wise Man",
          lastMessage: "Bonjour boss",
          lastTextTime: "Today",
          totalMessagesInChat: 15,
          blueCheck: false,
          lastSeen: "09:50",
          displayPicture:
            "https://www.cyphercoders.com/sites/default/files/default_images/default-user-icon-4.jpg",
          messages: [],
        },
        {
          id: 5,
          name: "Catherine",
          lastMessage: "Hey babe",
          lastTextTime: "Yesterday",
          totalMessagesInChat: 1,
          blueCheck: false,
          lastSeen: "online",
          displayPicture:
            "https://andybesttv.files.wordpress.com/2017/04/78fd2-18161354_105280080040548_4811051244892192768_n.jpg",
          messages: [
            {
              received: "Hey bb",
              sent: "Hey, sup?",
            },
            {
              received: "Nothing much, just got home, wbu?",
              sent: "Still at work!",
            },
            {
              received: "Oh, wow! what did you take for lunch today?",
              sent: "bread and spaghetti",
            },
            {
              received: "Yumm! Yammy, i guess you enjoyed, lol",
              sent: "Not really, was not enough for me.. lol😂😂",
            },
            {
              received: "😂 ... as much as i thought",
              sent: "... you know me!",
            },
          ],
        },
        {
          id: 6,
          name: "Mom",
          lastMessage: "How was your night?",
          lastTextTime: "Yesterday",
          totalMessagesInChat: 10,
          blueCheck: false,
          lastSeen: "14:13",
          displayPicture:
            "https://www.cyphercoders.com/sites/default/files/default_images/default-user-icon-4.jpg",
          messages: [],
        },
        {
          id: 7,
          name: "Elvis Pirata",
          lastMessage: "Nice work man",
          lastTextTime: "Yesterday",
          totalMessagesInChat: 3,
          blueCheck: false,
          lastSeen: "online",
          displayPicture:
            "https://www.cyphercoders.com/sites/default/files/default_images/default-user-icon-4.jpg",
          messages: [],
        },
      ],
    };
  },
  methods: {
    // getting the data from child component
    returnChatObject(chatObjectFromChildComponent) {
      console.log(chatObjectFromChildComponent);
      this.chatObjectToViewInInbox = chatObjectFromChildComponent;

      // setting the number of chats on the chat list to zero
      // when the user clicks on it to simulate whatsapp experience
      this.chatsList.map((item) => {
        // setting only for that particular element in array
        if (item.id == chatObjectFromChildComponent.id) {
          item.totalMessagesInChat = 0;
        }
      });
    },

    // function to filter chat list
    filterChatList(searchTerm) {
      console.log("searchTerm from child component => " + searchTerm);
    },
  },
  mounted: function () {
    // setting the first chat inbox with the first user in the array
    this.chatObjectToViewInInbox = this.chatsList[0];
    console.log(this.chatsList[0]);
  },
  // watch for changes in the array to update it like for ondelete of a chat action (so i can data with the furst chat)
  watch: {
    chatsList: function () {
      this.chatObjectToViewInInbox = this.chatsList[0]; // updating with the first chat in array
    },
  },
};
</script>
<style scoped>
.__sideChatList {
  height: 500px;
  overflow-y: scroll;
}

.__sideChatList::-webkit-scrollbar {
  width: 6px;
  height: 6px !important;
}
/* Track */
/* .__sideChatList::-webkit-scrollbar-track {
  box-shadow: inset 0 0 3px grey;
} */
/* Handle */
.__sideChatList::-webkit-scrollbar-thumb {
  background: rgba(0, 0, 0, 0.2);
}
/* Handle on hover */
/* .__sideChatList::-webkit-scrollbar-thumb:hover {
  background: rgb(156, 156, 156);
} */
.__chatItem {
  cursor: pointer;
}
</style>
