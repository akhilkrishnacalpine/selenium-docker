node {
	stage 'Repo download'
		checkout scm
	stage 'Build'
		sh '''
			cd test/
			mvn --batch-mode release:update-versions
			mvn versions:set -DnewVersion=${VERSION}
			mvn clean install -DskipTests 
		'''
	stage 'Archive' 
		archive 'test/target/nxpmp_test*.jar'
	stage 'Grid'
		sh '''
			cd $WORK_SPACE/Selenium-Grid
			docker-compose up -d
			[ $VALUE -gt 1 ] && docker-compose scale firefox=$VALUE chrome=$VALUE
			docker-compose ps
		'''	
	stage 'Test'
		sh '''
			mv test/target/nxpmp_test*.jar test/target/nxpmp_test.jar
			java -jar test/target/nxpmp_test.jar
		'''