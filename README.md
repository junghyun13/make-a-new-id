# make-a-new-id
# Step 1 Replace all uppercase letters in new_id with their lowercase counterparts. Step 2 Remove all characters from new_id except lowercase letters, numbers, minus (-), underscore (_), and period (.). Step 3 In new_id, a period (.) is replaced with a period (.) in which a period (.) is consecutive two or more times. Step 4 Remove the period (.) at the beginning or end of new_id, if any. Step 5 If new_id is an empty string, substitute "a" for new_id. Step 6 If new_id is more than 16 characters long, remove all but the first 15 characters of new_id. If a period (.) is located at the end of new_id after removal, the period (.) character located at the end is removed. Step 7 If new_id is 2 characters or less in length, append the last character of new_id repeatedly until new_id is 3 characters long. Let's go through the above steps and create a new ID! 1단계 new_id의 모든 대문자를 대응되는 소문자로 치환합니다. 2단계 new_id에서 알파벳 소문자, 숫자, 빼기(-), 밑줄(_), 마침표(.)를 제외한 모든 문자를 제거합니다. 3단계 new_id에서 마침표(.)가 2번 이상 연속된 부분을 하나의 마침표(.)로 치환합니다. 4단계 new_id에서 마침표(.)가 처음이나 끝에 위치한다면 제거합니다. 5단계 new_id가 빈 문자열이라면, new_id에 "a"를 대입합니다. 6단계 new_id의 길이가 16자 이상이면, new_id의 첫 15개의 문자를 제외한 나머지 문자들을 모두 제거합니다. 만약 제거 후 마침표(.)가 new_id의 끝에 위치한다면 끝에 위치한 마침표(.) 문자를 제거합니다. 7단계 new_id의 길이가 2자 이하라면, new_id의 마지막 문자를 new_id의 길이가 3이 될 때까지 반복해서 끝에 붙입니다. 위단계를 거쳐서 새로운 아이디를 만들어보자!
# python
def solution(new_id):
    new_id=new_id.lower() #step1
    answer=''
    for word in new_id: #2
        if word.islower() or word.isdigit() or word in ['-','_','.']:
            answer+=word
    while '..' in answer: #3
        answer=answer.replace('..','.')
    if answer[0]=='.': #4
        if len(answer)>=2:
            answer=answer[1:]
    if answer[-1]=='.': 
        answer=answer[:-1]
    if answer=='': #5
        answer='a'
    if len(answer)>=16: #6
        answer=answer[:15]
        if answer[-1]=='.':
            answer=answer[:-1]
    while len(answer)<3: #7
        answer+=answer[-1]
    return answer
new_id="...!@BaT#*..y.abcdefghijklm"
print(solution(new_id))
#result--> "bat.y.abcdefghi"
