
all: deps run

requests.json:
	curl https://cdn.cliqz.com/adblocking/requests_top500.json.gz | gunzip > requests.json

# VERSION: ebfc7b0300879ad44dba6a051c3c34b508b5a4f7
./blockers/adblockpluscore:
	git clone https://github.com/adblockplus/adblockpluscore.git ./blockers/adblockpluscore
	cd ./blockers/adblockpluscore && git reset --hard ebfc7b0300879ad44dba6a051c3c34b508b5a4f7

adblockpluscore: ./blockers/adblockpluscore

./node_modules/adblock-rs:
	npm install --no-save adblock-rs

adblock-rs: ./node_modules/adblock-rs

brave:
	NODE_ENV=production node run.js brave requests.json

cliqz:
	NODE_ENV=production node run.js cliqz requests.json

cliqz-compression:
	NODE_ENV=production node run.js cliqzCompression requests.json

ublock:
	NODE_ENV=production node run.js ublock requests.json

adblockplus:
	NODE_ENV=production node run.js adblockplus requests.json

tldts:
	NODE_ENV=production node run.js tldts requests.json

url:
	NODE_ENV=production node run.js url requests.json

adblockfast:
	NODE_ENV=production node run.js adblockfast requests.json

min:
	NODE_ENV=production node run.js min requests.json

deps:
	npm run prepare

run: deps url tldts cliqz ublock adblockplus brave adblockfast
